import numpy as np

# -------------------------------
# 1. POMDP Environment Setup
# -------------------------------
T = 20                    # Horizon
true_state = 0.0
state_noise_std = 0.1
obs_noise_std = 0.2
np.random.seed(1234)      # PEGASUS: deterministic seed

# -------------------------------
# 2. Policy Parameterization
# -------------------------------
theta = np.random.randn()  # Policy parameter (scalar)
alpha = 0.05               # Learning rate
n_iterations = 100

def policy(s, theta):
    """Linear Gaussian policy: a ~ N(theta * s, sigma^2)"""
    return np.random.normal(theta * s, 0.1)

def reward(s, a):
    """Quadratic reward: maximize proximity to target 1.0"""
    return - (s + a - 1.0)**2

# -------------------------------
# 3. REINFORCE Algorithm with PEGASUS
# -------------------------------
for it in range(n_iterations):
    s = true_state
    rewards, actions, states = [], [], []

    # --- Generate trajectory ---
    for t in range(T):
        y = s + np.random.normal(0, obs_noise_std)  # Noisy observation
        a = policy(y, theta)                         # Sample action
        s = s + a + np.random.normal(0, state_noise_std)
        r = reward(s, a)

        states.append(y)
        actions.append(a)
        rewards.append(r)

    # --- Compute discounted returns & policy gradient ---
    G = 0
    grads = []
    for t in reversed(range(T)):
        G = rewards[t] + 0.99 * G                  # Discounted return
        grad_log_pi = (actions[t] - theta*states[t]) * states[t] / (0.1**2)
        grads.append(grad_log_pi * G)

    # --- Update policy parameter ---
    theta += alpha * np.sum(grads)

print(f"Trained policy parameter: theta = {theta:.3f}")

# -------------------------------
# 4. Test Learned Policy
# -------------------------------
s = true_state
trajectory = []
for t in range(T):
    y = s + np.random.normal(0, obs_noise_std)
    a = policy(y, theta)
    s = s + a
    trajectory.append(s)

print("Final trajectory under learned policy:", trajectory)
