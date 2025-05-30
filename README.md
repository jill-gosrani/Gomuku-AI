# Gomoku-AI

_A Hybrid Neural Network + Minimax Agent for 15x15 Gomoku_

---

![Gomoku Board](https://en.wikipedia.org/wiki/Gomoku#/media/File:Renju.jpg)

---

## Table of Contents

- [Overview](#overview)
- [Team](#team)
- [Project Highlights](#project-highlights)
- [How It Works](#how-it-works)
  - [Neural Network Model](#neural-network-model)
  - [Custom Minimax Heuristic](#custom-minimax-heuristic)
- [Performance & Results](#performance--results)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Contributions](#contributions)
- [Contact](#contact)

---

## Overview

**Gomoku-AI** is an advanced artificial intelligence agent designed to play Gomoku on a 15x15 board. Our project leverages the synergy of a custom Convolutional Neural Network (CNN) and a bespoke minimax heuristic. The neural network learns from thousands of real game states, while the minimax algorithm ensures robust, tactical play when the neural network is uncertain. This hybrid approach delivers both adaptability and strategic depth, making our AI a formidable opponent.

---

## Team

- [Jill Gosrani](https://github.com/jill-gosrani)
- [Pavan Pandya](https://github.com/Pavan-Pandya1)

---

## Project Highlights

- **Hybrid AI:** Combines a trained CNN with a custom minimax algorithm for move selection.
- **Dynamic Heuristics:** The minimax function evaluates board states in all directions, with dynamic scoring based on game progression.
- **Proactive Defense:** The AI anticipates threats and blocks opponents up to two moves in advance.
- **Adaptive Play:** The neural network adapts to varied strategies, while minimax ensures fallback reliability.
- **Competitive Performance:** Achieves a 75% ±5% win rate against baseline AIs.

---

## How It Works

### Neural Network Model

- **Data:** Trained on 2,880 real game states from the Gomo-cup 2022.
- **Architecture:** Six-layer sequential CNN (64 → 128 → 256 → 128 → 64), all with ReLU activations.
- **Output:** 1x1 convolution + reshape + sigmoid for binary classification.
- **Optimizer:** Adam (outperformed SGD in our tests).
- **Training:** 20 epochs, reaching ~84% accuracy and 0.042 loss.

### Custom Minimax Heuristic

- **Evaluation:** Scans the board in all directions, scoring based on consecutive pieces and potential threats.
- **Weighting:** Scores increase as the board fills, emphasizing endgame scenarios.
- **Player Roles:** The MIN player is aggressive, seeking early wins; the MAX player is defensive, blocking threats.
- **Fallback Logic:** If the neural network suggests an invalid move, minimax takes over for optimal decision-making.

---

## Performance & Results

- **Average Win Rate:** 75% (±5%) over multiple games versus baseline AIs.
- **Consistency:** Model exhibits strong adaptability and resilience.
- **Training Insights:** Reducing layers led to overfitting; combining model and minimax at depth limits improved accuracy but increased computation.

---

## Project Structure

```
├── compete.py                  # Run games between two agents (human or AI)
├── performance.py              # Benchmark AI performance, save results to perf.pkl
├── gomoku.py                   # Core game logic and board management
├── perf.pkl                    # Saved benchmark results
├── report_gomokuAI.pdf         # Project report
├── README.md                   # Project README
├── policies/                   # Player agents
│   ├── __init__.py
│   ├── human.py                # Human player interface
│   ├── minimax.py              # Minimax agent
│   ├── random.py               # Random move agent
│   ├── submission.py           # Hybrid CNN + minimax agent (main AI)
│   ├── model_2800_20epoch      # Model file
│   ├── README.md
│   └── CNN+model/
│       ├── model_creation/
│       │   ├── config/
│       │   ├── dataset/
│       │   │   └── gomocup2019results
│       │   ├── create_dataset.py
│       │   ├── gomoku.py
│       │   ├── gui.py
│       │   ├── read_dataset.py
│       │   ├── README-md.txt
│       │   ├── result.png
│       │   └── train_AI_Project.ipynb
│       └── models/
```

---

## Usage

**Play a game (15x15 board, 5 in a row to win):**

python3 compete.py -b 15 -w 5 -x Human -o Minimax

- `-x` specifies the max player (e.g., Human)
- `-o` specifies the min player (e.g., Minimax)
- Policy names are case-sensitive: `Human`, `Random`, `Minimax`, `Submission`

**Run performance benchmarks:**

python3 performance.py

- Runs 30 games and outputs performance statistics.

---

## Contributions

Both I and Pavan Pandya contributed equally to the design, coding, and integration of the neural network and minimax heuristic, with primary development in:

- `policies/submission.py` (hybrid agent logic)
- `policies/CNN+model/` (model architecture, data preparation, training)

---

## Contact

For questions, feedback, or collaboration, reach out via [Jill Gosrani](https://www.linkedin.com/in/jill-gosrani/) or [Pavan Pandya](https://www.linkedin.com/in/pavan-pandya/).

---

_This project was developed as part of the CIS667 (Introduction to Artificial Intelligence) Final Project, Fall 2023._
