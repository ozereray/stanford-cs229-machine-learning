import numpy as np
import matplotlib.pyplot as plt

# --- 1. System Definition ---
# Linear dynamics: s_{t+1} = A s_t + B a_t + w_t
A = np.array([[1.0, 1.0],
              [0.0, 1.0]])
B = np.array([[0.0],
              [1.0]])

# Observation model: y_t = C s_t + v_t
C = np.eye(2)  # Direct observation of position and velocity
Sigma_w = np.array([[0.01, 0.0],
                    [0.0, 0.01]])  # Process noise covariance
Sigma_v = np.array([[0.05, 0.0],
                    [0.0, 0.05]])  # Measurement noise covariance

# Quadratic cost matrices (LQR)
U = np.eye(2)        # State cost
V = np.array([[0.01]])  # Control cost

T = 50  # Horizon

# --- 2. LQR via Riccati Equation ---
n = A.shape[0]
d = B.shape[1]

Phi = [None]*(T+1)
L = [None]*T
Phi[T] = U

for t in reversed(range(T)):
    L[t] = -np.linalg.inv(V + B.T @ Phi[t+1] @ B) @ (B.T @ Phi[t+1] @ A)
    Phi[t] = U + A.T @ Phi[t+1] @ (A + B @ L[t])

# --- 3. Kalman Filter Initialization ---
s_true = np.array([[5.0], [0.0]])  # True initial state
s_hat = np.array([[0.0], [0.0]])   # Estimated initial state
P = np.eye(2)                       # Initial estimation covariance

states_true = [s_true.copy()]
states_est = [s_hat.copy()]
actions = []
observations = []

# --- 4. Simulation Loop ---
for t in range(T):
    # --- Control using estimated state ---
    a = L[t] @ s_hat
    actions.append(a.item())
    
    # --- True system update ---
    w = np.random.multivariate_normal(np.zeros(n), Sigma_w).reshape(-1,1)
    s_true = A @ s_true + B @ a + w
    states_true.append(s_true.copy())
    
    # --- Observation ---
    v = np.random.multivariate_normal(np.zeros(n), Sigma_v).reshape(-1,1)
    y = C @ s_true + v
    observations.append(y.copy())
    
    # --- Kalman Filter Predict ---
    s_pred = A @ s_hat + B @ a
    P_pred = A @ P @ A.T + Sigma_w
    
    # --- Kalman Filter Update ---
    K = P_pred @ C.T @ np.linalg.inv(C @ P_pred @ C.T + Sigma_v)
    s_hat = s_pred + K @ (y - C @ s_pred)
    P = (np.eye(n) - K @ C) @ P_pred
    states_est.append(s_hat.copy())

# Convert lists to arrays for plotting
states_true = np.hstack(states_true)
states_est = np.hstack(states_est)
observations = np.hstack(observations)
actions = np.array(actions)

# --- 5. Plot Results ---
plt.figure(figsize=(12,5))
plt.subplot(1,2,1)
plt.plot(states_true[0,:], label='True Position')
plt.plot(states_est[0,:], '--', label='Estimated Position')
plt.plot(states_true[1,:], label='True Velocity')
plt.plot(states_est[1,:], '--', label='Estimated Velocity')
plt.title("LQG State Estimation")
plt.xlabel("Time step")
plt.legend()

plt.subplot(1,2,2)
plt.plot(actions, label='Control Input a_t')
plt.title("LQR Control Actions (using KF estimates)")
plt.xlabel("Time step")
plt.ylabel("a_t")
plt.legend()
plt.tight_layout()
plt.show()
