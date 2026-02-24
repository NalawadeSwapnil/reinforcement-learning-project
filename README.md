# ConnectX Reinforcement Learning: Q-Learning vs SARSA(λ)

A comparative study of two reinforcement learning algorithms — Q-learning and SARSA(λ) — applied to the ConnectX game environment.

This project trains agents to learn optimal strategies through interaction with the environment and evaluates their performance against random, rule-based (Negamax), and self-play opponents.

---

## Overview

This project implements and evaluates two reinforcement learning algorithms:

- Q-learning (Off-policy)
- SARSA(λ) (On-policy with eligibility traces)

The environment is a modified ConnectX game:

- Grid size: 4 rows × 5 columns
- Win condition: Connect 3 tokens
- Reward system:
  - Win = +1
  - Loss = -1
  - Draw = 0

Agents were trained in two phases:
1. Against a Random agent
2. Against a Negamax agent (deterministic rule-based opponent)

Performance was measured using reward curves, evaluation matches, and learned Q-table heatmaps.

---

## Algorithms Implemented

### Q-Learning
- Off-policy learning algorithm
- Updates Q-values assuming optimal future action
- Faster convergence
- More aggressive and reward-seeking

### SARSA(λ)
- On-policy learning algorithm
- Uses eligibility traces to reinforce recent state-action pairs
- More stable and gradual learning
- Learns based on actual actions taken

---

## Training Setup

Each agent was trained under the following conditions:

| Agent        | Opponent  | Role        | Episodes |
|--------------|-----------|------------|----------|
| Q-learning   | Random    | P1 & P2    | 1000 each |
| Q-learning   | Negamax   | P1 & P2    | 1000 each |
| SARSA(λ)     | Random    | P1 & P2    | 1000 each |
| SARSA(λ)     | Negamax   | P1 & P2    | 1000 each |

Additional details:
- Epsilon-greedy exploration (epsilon decayed from 1.0)
- Legal action handling to prevent invalid moves
- Class-based agent structure with `act()` and `learn()` methods

---

## Results Summary

### Performance vs Random Agent

After training against Negamax:

**Q-learning**
- Win rate improved from 50% → 56%
- Strong improvement as Player 2
- Slight drop when starting first

**SARSA(λ)**
- Win rate improved from 54% → 56%
- More stable performance
- Slight drop in self-play after stronger training

---

### Performance vs Negamax

Both agents initially struggled against Negamax due to its optimal deterministic policy.

After training:
- Q-learning improved from 4% → 8% win rate
- SARSA(λ) improved from 2% → 8% win rate

---

### Head-to-Head Evaluation

100 evaluation games were played in both directions.

- Q-learning won 68/100 games against SARSA(λ)
- SARSA(λ) won 64/100 games in reverse setup
- No draws occurred

Q-learning demonstrated stronger direct competitive performance.

---

## Learned Policies (Heatmap Insights)

Both agents strongly preferred the center column (Column 2), indicating learning of optimal central positioning.

- Q-learning showed sharper concentration in Columns 1–3
- SARSA(λ) displayed more evenly distributed column preferences

This reflects:
- Q-learning → more aggressive exploitation
- SARSA(λ) → more cautious exploration

---

## Key Takeaways

- Q-learning converges faster but may overestimate early values.
- SARSA(λ) provides more stable and realistic learning behavior.
- Training across both player roles is essential for fair evaluation.
- Legal move handling significantly improves training stability.

---

## Technologies Used

- Python
- Kaggle Environments (ConnectX)
- NumPy
- Matplotlib

---

## How to Run

1. Install dependencies:
```
pip install kaggle-environments numpy matplotlib
```

2. Run the notebook or Python script:
```
python main.py
```
(or open and execute the Jupyter notebook)

---

## References

- Sutton, R. S., & Barto, A. G. (2018). Reinforcement Learning: An Introduction. MIT Press.
- Alderton, E., Wopat, E., & Koffman, J. (2021). Reinforcement Learning for Connect Four.
- Kochenderfer, M. J. (2015). Decision Making Under Uncertainty.
- Kaggle Environments API Documentation

---

## Author

Swapnil S Nalawade  

