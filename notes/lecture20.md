import numpy as np

# --- 1. Environment (Simple 1D POMDP) ---
T = 20  # Horizon
true_state = 0.0
state_noise_std = 0.1
obs_noise_std = 0.2
np.random.seed(42)  # PEGASUS: deterministic seeds

# --- 2. Policy Parameterization ---
theta = np.random.randn()  # scalar policy parameter
alpha = 0.05  # learning rate
n_iterations = 100

def policy(s, theta):
    """Linear stochastic policy: Gaussian with mean theta*s"""
    mean = theta * s
    return np.random.normal(mean, 0.1)  # action a_t

def reward(s, a):
    """Reward function: reward for reaching target state = 1.0"""
    return - (s + a - 1.0)**2  # maximize reward at s+a ≈ 1

# --- 3. REINFORCE Algorithm ---
for it in range(n_iterations):
    s = true_state
    rewards = []
    actions = []
    states = []
    
    # Generate trajectory
    for t in range(T):
        # Observation with noise
        y = s + np.random.normal(0, obs_noise_std)
        a = policy(y, theta)
        s = s + a + np.random.normal(0, state_noise_std)
        r = reward(s, a)
        
        states.append(y)
        actions.append(a)
        rewards.append(r)
    
    # Compute total return
    G = 0
    grads = []
    for t in reversed(range(T)):
        G = rewards[t] + 0.99*G  # discounted return
        grad_log_pi = (actions[t] - theta*states[t]) * states[t] / (0.1**2)
        grads.append(grad_log_pi * G)
    
    # Update policy
    theta += alpha * np.sum(grads)
    
print(f"Trained policy parameter theta: {theta:.3f}")

# --- 4. Test Policy ---
s = true_state
trajectory = []
for t in range(T):
    y = s + np.random.normal(0, obs_noise_std)
    a = policy(y, theta)
    s = s + a
    trajectory.append(s)

print("Final trajectory under learned policy:", trajectory)
