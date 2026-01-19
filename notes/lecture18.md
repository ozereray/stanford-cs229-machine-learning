import numpy as np
import matplotlib.pyplot as plt

# --- 1. LQR Environment Setup ---
# Discrete-time linear system: s_{t+1} = A s_t + B a_t
A = np.array([[1.0, 1.0],
              [0.0, 1.0]])  # State transition matrix
B = np.array([[0.0],
              [1.0]])      # Control matrix

# Quadratic cost matrices
U = np.eye(2)   # State cost
V = np.array([[0.01]])  # Control cost

# Horizon
T = 50  # Time steps

# --- 2. Backward Riccati Recursion to compute optimal L_t ---
n = A.shape[0]
d = B.shape[1]

Phi = [None] * (T+1)
Psi = [None] * (T+1)
L = [None] * T

# Terminal cost
Phi[T] = U
Psi[T] = 0

# Backward recursion
for t in reversed(range(T)):
    # Compute L_t = -(V + B^T Phi B)^-1 B^T Phi A
    L[t] = -np.linalg.inv(V + B.T @ Phi[t+1] @ B) @ (B.T @ Phi[t+1] @ A)
    # Update Phi using Riccati equation
    Phi[t] = U + A.T @ Phi[t+1] @ (A + B @ L[t])
    Psi[t] = 0  # For simplicity, scalar term ignored

# --- 3. Simulate system with optimal policy ---
s = np.array([[5.0], [0.0]])  # Initial state
states = [s.copy()]
actions = []

for t in range(T):
    a = L[t] @ s
    actions.append(a.item())
    s = A @ s + B @ a
    states.append(s.copy())

states = np.hstack(states)

# --- 4. Plot results ---
plt.figure(figsize=(10,4))
plt.subplot(1,2,1)
plt.plot(states[0,:], label='Position')
plt.plot(states[1,:], label='Velocity')
plt.title("State Evolution")
plt.xlabel("Time step")
plt.legend()

plt.subplot(1,2,2)
plt.plot(actions, label='Control Input')
plt.title("Control Action Over Time")
plt.xlabel("Time step")
plt.ylabel("a_t")
plt.legend()

plt.tight_layout()
plt.show()
