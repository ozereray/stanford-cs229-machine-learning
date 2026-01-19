import numpy as np
import matplotlib.pyplot as plt

# --- 1. System Definition ---
# Continuous-state linear system s_{t+1} = A s_t + B a_t + w_t
A = np.array([[1.0, 1.0],
              [0.0, 1.0]])  # State transition matrix
B = np.array([[0.0],
              [1.0]])      # Control matrix

# Quadratic cost matrices
U = np.eye(2)      # State cost
V = np.array([[0.01]])  # Control cost

# Horizon
T = 50

# --- 2. Discrete-Time Riccati Equation Backward Pass ---
n = A.shape[0]
d = B.shape[1]

Phi = [None]*(T+1)
Psi = [None]*(T+1)
L = [None]*T

# Terminal cost
Phi[T] = U
Psi[T] = 0

for t in reversed(range(T)):
    # Compute optimal linear feedback
    L[t] = -np.linalg.inv(V + B.T @ Phi[t+1] @ B) @ (B.T @ Phi[t+1] @ A)
    # Update value function
    Phi[t] = U + A.T @ Phi[t+1] @ (A + B @ L[t])
    Psi[t] = 0  # Ignored scalar term for simplicity

# --- 3. Simulation with Noise ---
s = np.array([[5.0], [0.0]])  # Initial state
states = [s.copy()]
actions = []

# Add Gaussian process noise
noise_std = 0.05

for t in range(T):
    a = L[t] @ s
    actions.append(a.item())
    w = np.random.normal(0, noise_std, size=(2,1))  # Process noise
    s = A @ s + B @ a + w
    states.append(s.copy())

states = np.hstack(states)

# --- 4. Plot Results ---
plt.figure(figsize=(10,4))
plt.subplot(1,2,1)
plt.plot(states[0,:], label='Position')
plt.plot(states[1,:], label='Velocity')
plt.title("LQR State Evolution")
plt.xlabel("Time step")
plt.legend()

plt.subplot(1,2,2)
plt.plot(actions, label='Control Input')
plt.title("LQR Control Actions")
plt.xlabel("Time step")
plt.ylabel("a_t")
plt.legend()

plt.tight_layout()
plt.show()
