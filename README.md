# Project 3: Reinforcement Learning

UC Berkeley CS 188 Pacman AI project focused on reinforcement learning. Students implement value iteration and Q-learning agents, then apply them to Gridworld, a simulated robot crawler, and Pacman.

## Student Files to Edit

- `valueIterationAgents.py` - Value iteration agent for Gridworld
- `qlearningAgents.py` - Q-learning agents for Gridworld, Crawler, and Pacman
- `analysis.py` - Answers to analysis questions (parameter tuning)

## Running

### Gridworld (manual control)

```bash
python3 gridworld.py -m
```

### Autograder

```bash
python3 autograder.py
```

Grade a specific question:

```bash
python3 autograder.py -q q1
```

### Crawler

```bash
python3 crawler.py
```

### Pacman with Q-learning

```bash
python3 pacman.py -p PacmanQAgent -x 2000 -n 2010 -l smallGrid
```

## Key Concepts

- **Value Iteration** (offline planning): computes optimal policy from a known MDP
- **Q-Learning** (online learning): learns action values from experience without a model
- **Epsilon-Greedy**: exploration strategy balancing random exploration with learned policy
- **Approximate Q-Learning**: uses feature extractors to generalize across states

## Questions Implemented

- **Question 1: Value Iteration**: Implemented an offline planner using batch value iteration. For a fixed number of iterations, it applies the Bellman update equation across all states to compute k-step estimates of optimal values.
- **Question 2: Bridge Crossing Analysis**: Fine-tuned the `noise` parameter to `0.0` to encourage the agent to attempt to cross a narrow bridge with high-penalty chasms on either side, ensuring it moves exactly as intended.
- **Question 3: Policies**: Configured gridworld MDP parameters (discount factor, noise, and living reward) to produce optimal policies that either preferred close/distant exits or risked/avoided the negative reward cliff.
- **Question 4: Asynchronous Value Iteration**: Implemented an alternative to batch value iteration that updates the value of only a single state per iteration, cycling through the state space sequentially.
- **Question 5: Prioritized Sweeping Value Iteration**: Optimized asynchronous value iteration by using a priority queue. It prioritizes updating states whose current value differs significantly from their target value (maximum Q-value).
- **Question 6: Q-Learning**: Created a generic, model-free reinforcement learning agent that estimates Q-values online by observing transitions and applying the Q-learning update rule.
- **Question 7: Epsilon Greedy**: Augmented the Q-learning agent with an epsilon-greedy strategy for action selection. The agent explores randomly with probability `epsilon`, and otherwise exploits its current best learned policy.
- **Question 8: Bridge Crossing Revisited**: Analyzed whether an epsilon-greedy Q-learner could reliably learn the BridgeGrid in 50 iterations. I concluded this is `NOT POSSIBLE`, as random exploration inevitably leads the agent into the high-penalty abyss early in training, discouraging further attempts to cross.
- **Question 9: Q-Learning and Pacman**: Applied the Q-learning agent to the Pacman environment. The agent successfully learned to win games on small boards by continuously updating its state-action values.
- **Question 10: Approximate Q-Learning**: Scaled Q-learning to larger boards by implementing a feature-based approximate Q-learning agent. Instead of storing values for every distinct state, it learns weights for generalized features (e.g., closest food distance), drastically accelerating training and reducing memory.

## Project Structure

| File | Description |
|------|-------------|
| `mdp.py` | MDP interface definition |
| `environment.py` | Environment interface |
| `learningAgents.py` | Base classes for learning agents |
| `featureExtractors.py` | Feature extractors for approximate Q-learning |
| `gridworld.py` | Gridworld MDP implementation and main driver |
| `crawler.py` | Crawler robot simulation |
| `pacman.py` | Pacman game engine |
| `autograder.py` | Project autograder |
| `test_cases/` | Test cases for each question |

## Attribution

The Pacman AI projects were developed at UC Berkeley by John DeNero and Dan Klein. Student-side autograding by Brad Miller, Nick Hay, and Pieter Abbeel. More info at http://ai.berkeley.edu.
