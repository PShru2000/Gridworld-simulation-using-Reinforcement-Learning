# Simulating a Four Rooms Gridworld Environment using Reinforcement Learning

### Environment Setup for Four Rooms Simulation

This section outlines the setup for the Four Rooms simulation environment used to test reinforcement learning policies. The environment is designed to mimic a gridworld with walls and a probability of action slippage, providing a platform to assess the robustness and effectiveness of different learning algorithms.

#### State Space
- The environment is a grid with coordinates (x, y where x ∈ [0, 10] and y ∈ [0, 10]
- There are walls within the grid, represented as shaded cells, that the agent cannot occupy

#### Actions
- The agent has four possible actions: LEFT,DOWN, RIGHT, and UP
- Actions are allowed from any non-wall state within the grid boundaries

#### Transition Dynamics
- Actions result in movement in the intended direction with a probability of 0.9
- With a probability of 0.05, the agent may move perpendicularly to the intended direction (e.g., if intending to move RIGHT, the agent may slip and move UP or DOWN instead)
- If an action would result in collision with a wall or moving out of bounds, the agent's state remains unchanged.

#### Starting and Goal States
- The agent begins each episode at the starting state (0, 0)
- The goal state is (10, 10). Reaching this state yields a reward and teleports the agent back to the start

#### Rewards
- Achieving the goal state (10, 10) grants a reward of +1
- All other transitions yield a reward of 0

#### Special Cases
- From state (0, 10), moving UP will result in (0, 10) with 0.95 probability and (1, 10) with 0.05 probability, with a reward of 0

#### Agent and Policy Interaction
- The agent interacts with the environment by providing actions based on a policy.
- The policy is a manual state-action mapping π: S → A, which can be user-defined for testing.

## Gridworld Environment

![Screenshot](https://github.com/PShru2000/Gridworld-simulation-using-Reinforcement-Learning/blob/main/env.png?raw=true)
