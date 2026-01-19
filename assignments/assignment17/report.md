import numpy as np
from sklearn.linear_model import LinearRegression

# --- Environment Setup ---
class ContinuousMDP:
    def __init__(self, state_dim=1, action_space=[-1, 0, 1], noise_std=0.1):
        self.state_dim = state_dim
        self.action_space = action_space
        self.noise_std = noise_std

    def step(self, s, a):
        """Simulated dynamics: s' = s + a + noise"""
        noise = np.random.randn(self.state_dim) * self.noise_std
        s_next = s + a + noise
        # Reward: penalize distance from target (0)
        reward = -np.sum(s_next**2)
        return s_next, reward

# --- Fitted Value Iteration ---
def fitted_value_iteration(env, n_iterations=20, n_samples=100, gamma=0.9):
    state_samples = np.random.uniform(-5, 5, size=(n_samples, env.state_dim))
    V = np.zeros(n_samples)  # Initial value
    reg = LinearRegression()

    for it in range(n_iterations):
        targets = np.zeros(n_samples)
        for i, s in enumerate(state_samples):
            q_values = []
            for a in env.action_space:
                s_next, r = env.step(s, a)
                # Find closest sampled state for current approximation
                closest_idx = np.argmin(np.linalg.norm(state_samples - s_next, axis=1))
                q_values.append(r + gamma * V[closest_idx])
            targets[i] = max(q_values)
        # Fit value function approximation
        reg.fit(state_samples, targets)
        V = reg.predict(state_samples)
        print(f"Iteration {it+1}, max V: {np.max(V):.2f}")

    return reg

# --- Usage ---
env = ContinuousMDP()
value_model = fitted_value_iteration(env)

# Test: evaluate value for new state
s_test = np.array([[2.0]])
V_est = value_model.predict(s_test)
print(f"Estimated V({s_test[0][0]}) = {V_est[0]:.2f}")
