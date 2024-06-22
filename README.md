# Grid World Solver using Q-Learning

## Introduction
This project demonstrates the application of Q-learning and Double Q-learning algorithms to solve a grid world problem. The grid world contains an agent, a goal, a silver item, and a fire. The objective is to navigate the agent to the goal while collecting silver for extra points and avoiding fire which terminates the game.

## Environment Description

### Elements:
- **Agent:** Can perform 4 actions: down, up, right, and left, encoded as [0, 1, 2, 3].
- **Fire:** If the agent lands on fire, the game ends and the agent loses.
- **Silver:** Collecting silver grants points but it disappears after being collected.
- **Goal:** Reaching the goal ends the game and the agent wins.
![image](https://github.com/imalhotra15/Q-Learning-Grid-World/assets/118845522/fffc5955-4ca7-4856-92d9-0bca75681ace)

### Environment Types:
#### Deterministic Environment:
- The next state is exactly determined by the current state and action without any uncertainty.
- \( P(s', r | s, a) = 1 \)

#### Stochastic Environment:
- The next state is determined by the current state and action only 80% of the time. The remaining 20% of the time, the action is random.
- For instance, if the agent is at [2,0] and performs action 'left' (encoded as 3), in a stochastic environment, there's a 20% chance it could perform a different action, like moving 'down' (encoded as 0).

### Comparison:
In a **deterministic environment**, the outcome of an action is predictable and consistent, leading to straightforward policy development. In a **stochastic environment**, there is inherent uncertainty, making the task more challenging as the agent must adapt to unpredictable outcomes.

## Q-Learning and Double Q-Learning

### Overview:
- **Q-Learning:** A model-free, off-policy algorithm that updates Q-values using the Bellman equation:
  \[ Q(s, a) = Q(s, a) + \alpha \cdot (r + \gamma \cdot \max(Q(s', a')) - Q(s, a)) \]
- **Double Q-Learning:** A variant of Q-learning that uses two Q-value tables to reduce overestimation bias.

### Implementation Details:
- **State Representation:** Each grid cell is a unique state.
- **Action Space:** The agent can move in four directions: up, down, left, right.
- **Rewards:** 
  - Goal: +100
  - Silver: +10
  - Fire: -20
  - Empty Tile: -1
  - Hitting the Wall: -3

### Results:
1. **Variability:** In stochastic environments, rewards show higher variability due to the unpredictable nature of state transitions.
2. **Convergence:** Deterministic environments converge faster (around 500 episodes) compared to stochastic ones, which continue to show reward variability even after 1000 episodes.
3. **Performance:** In actual games, Q-tables for both environment types perform similarly, scoring high cumulative rewards despite starting position differences.
4. **Comparison:** Double Q-learning shows less variability in cumulative rewards over time compared to Q-learning.

![image](https://github.com/imalhotra15/Q-Learning-Grid-World/assets/118845522/f07c8bff-9811-43a1-9ea7-3f81c555d2df)

![image](https://github.com/imalhotra15/Q-Learning-Grid-World/assets/118845522/347bff69-b837-4c86-b62a-b704e3da6f96)


## Hyperparameter Tuning

Using the `Optuna` module, we tuned several parameters to optimize performance:
1. **Number of Episodes**
2. **Minimum Epsilon Value**

## Notes

This was done as a part of the coursework of CSE 574 at the University at Buffalo. The source code is not available publicly to avoid academic integrity violations. Please feel free to contact the author if you wish access to the source code.
