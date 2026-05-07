
This project implements **Q-Learning**, a fundamental off-policy reinforcement learning algorithm, to navigate the **CliffWalking-v1** environment. Unlike SARSA, Q-Learning is "greedy" in its updates, estimating the value of the optimal policy independently of the agent's actual actions.

**Technical Details**
* **Algorithm**: Q-Learning (Off-Policy Temporal Difference Learning).
* **Environment**: `CliffWalking-v1` from the **Gymnasium** library.
* **State Space**: Discrete(48), representing a $4 \times 12$ grid.
* **Action Space**: Discrete(4) (0: Up, 1: Right, 2: Down, 3: Left).
* **Hyperparameters**:
    * **Learning Rate ($\alpha$):** 0.5.
    * **Discount Factor ($\gamma$):** 0.99.
    * **Exploration Rate ($\epsilon$):** 0.1 ($\epsilon$-greedy policy).
    * **Total Episodes:** 500.
Implementation HighlightS
* **Q-Table Storage**: Uses a $48 \times 4$ NumPy array to store and iterate on state-action pairs.
* **Off-Policy Update Rule**: Implements the Q-Learning update equation:
    $$Q(s, a) \leftarrow Q(s, a) + \alpha [r + \gamma \max_{a'} Q(s', a') - Q(s, a)]$$.
* **Dynamic Rendering**: Features a training loop that switches to `human` render mode every 50 episodes to visualize the agent's learning progress in real-time.
* **Epsilon-Greedy Strategy**: Balances the exploration of the grid with the exploitation of the highest-value Q-values.

#### **Results**
* **Learning Efficiency**: The agent quickly transitions from exploratory failure (high negative rewards like -1705) to consistent success.
* **Optimization**: After 500 episodes, the agent converges to a total reward of approximately **-13 to -15**, reflecting an optimized path that minimizes steps while avoiding the -100 cliff penalty.
* **Inference**: The final evaluation cell demonstrates the agent's ability to navigate the grid in just 13-15 steps using the learned Q-values.

