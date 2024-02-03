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

## Problem Statement

1) Implement a simulate function that acts as the Four Rooms environment,It should take in the current state s and desired action a, and return the next state s′ as well as the reward r

2) Implement a manual policy, and an agent that interacts with the simulator and the policy

3) Implement a random policy. A random policy outputs one of the four actions, uniformly at random. This is an example of a stochastic policy.

4) Devise and implement at least two more policies, one of which should be generally worse than the random policy, and one better


## Implementation Process

Four Rooms Gridworld is a classic RL problem that involves navigating an agent through a grid with obstacles to reach a goal. The following steps outline the process for setting up and interacting with the Four Rooms Gridworld environment:

#### Step 1: Initializing the Environment
- Start by defining the grid space with walls and open spaces, marking the starting state (0, 0) and the goal state (10, 10).

#### Step 2: Defining State Space and Actions
- The state is represented by (x, y) coordinates within the grid.
- The agent can perform four actions: LEFT, DOWN, RIGHT, and UP.

#### Step 3: Implementing Transition Dynamics
- When an action is chosen, there is a 90% chance the agent moves in the intended direction.
- There is a 5% chance the agent slips and moves perpendicularly to the intended direction.
- If an action would result in a wall collision or moving out of bounds, the agent stays in the current state.

#### Step 4: Simulating Agent Movement
- Created a simulate function to handle the logic for state transitions and reward assignments.
- The function should accept the current state and action, then return the new state and reward.

#### Step 5: Handling Goal State and Rewards
- Set the reward for reaching the goal state to +1, and 0 for all other transitions.
- Implemented the teleportation mechanism to reset the agent to the start state upon reaching the goal.

#### Step 6: Agent-Policy Interaction
- Developed a manual policy or automated algorithm to decide actions based on the current state.
- Used this policy to test the agent’s ability to navigate through the grid to the goal state.

#### Step 7: Environment Testing
- Manually tested the environment with predetermined actions to ensure the transition dynamics are as expected.
- Ran automated tests with your policy or RL algorithm to evaluate performance.

#### Step 8: Analysis
- Recorded the number of steps taken to reach the goal and the frequency of reaching the goal within a set number of steps.
- Analyzed the data to assess the effectiveness of the policy or learning algorithm.

#### Step 9: Visualization
- Create visualizations such as state transition diagrams or learning curves to represent the agent's performance.
- Summarized the findings and report on the agent’s learning progress and challenges encountered.

#### Step 10: Iteration and Optimization
- Based on the performance, iterate on the policy or algorithm to improve the agent’s navigation strategy.
- Experimented with different reward structures, slip probabilities, and action sets to optimize the agent’s learning efficiency.


## Result Analysis

Please refer to the **[outputs](https://github.com/PShru2000/Gridworld-simulation-using-Reinforcement-Learning/tree/main/Outputs-RL1)** for the resuts

**Better Policy:**

-Demonstrates a strong performance, with a steady increase in the cumulative reward over time
-The average curve is consistently higher than the other policies, indicating that this policy more frequently makes decisions that lead to rewards
-The variation between trials is relatively small, suggesting that the Better Policy is robust and reliable

**Random Policy:**

-As expected, the Random Policy shows a gradual and less steep increase in cumulative rewards. This is indicative of the lack of strategy, relying on chance for successful outcomes
-There is more variability between trials compared to the Better Policy, which is consistent with the stochastic nature of random decisions

**Worse Policy**

-The Worse Policy curve is nearly flat, with very minimal increase in cumulative rewards. This suggests the policy often makes decisions that do not lead to rewards, and may frequently hit penalties or take suboptimal paths
-There is some variation between trials, but the general trend indicates poor performance

**Overall Observations**

-The Better Policy is evidently the most effective, consistently achieving higher rewards at a quicker rate than the other policies. It is likely making intelligent choices that navigate the agent towards higher-reward states

-The Random Policy reflects the uncertainty and lack of direction in its decision-making process, leading to a much slower accumulation of rewards. However, it still outperforms the Worse Policy due to the random chance of encountering rewards

-The Worse Policy demonstrates what not to do in this environment. Its performance suggests it may be consistently making the worst possible decision at each step, or it could be stuck in low-reward states due to poor navigation choices
