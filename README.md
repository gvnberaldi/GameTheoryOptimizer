# Optimizing Game Theory Algorithms for Graph-Based Games

## Overview
This project investigates computational methods for two key solution concepts in game theory:
- **Shapley Value** for coalitional games.
- **Nash Equilibria** for non-cooperative games.

We demonstrate that leveraging specific properties of graph-based games can significantly speed up the computation of these solution concepts. Additionally, we implement a mechanism design to incentivize truthful reporting in weighted path games.

## Features
### 1. **Shapley Value Computation**
- **Setting**: A graph-based coalitional game where the value of a coalition depends on forming a path between two special nodes \( s \) and \( t \).
- **Objective**: Fairly distribute the coalition's worth among players.
- **Key Innovation**: Optimize the characteristic function representation by only storing winning coalitions.
- **Results**:
  - For both dense and sparse graphs, the optimized approach outperformed the naive approach by an order of magnitude.

![Shapley Value Sparse Graphs](path/to/sparse_shapley_plot.png)
*Figure 1: Shapley Value computation for sparse graphs.*

![Shapley Value Dense Graphs](path/to/dense_shapley_plot.png)
*Figure 2: Shapley Value computation for dense graphs.*

### 2. **Nash Equilibria Computation**
- **Setting**: A non-cooperative game where agents decide to cooperate or defect.
- **Payoff Structure**:
  - Cooperative agents gain if a path forms and have fewer than three cooperating neighbors.
  - Defectors incur a penalty in all cases.
- **Key Innovation**: Reduce the number of strategy profiles to check by pre-selecting always-cooperating nodes.
- **Results**:
  - Sparse graphs benefit significantly from the optimized solution.
  - Dense graphs show minimal improvement due to high connectivity.

![Nash Equilibria Sparse Graphs](path/to/sparse_nash_plot.png)
*Figure 3: Nash Equilibria computation for sparse graphs.*

![Nash Equilibria Dense Graphs](path/to/dense_nash_plot.png)
*Figure 4: Nash Equilibria computation for dense graphs.*

### 3. **Tree Decomposition for Nash Equilibria**
- **Approach**: Use tree decomposition to propagate candidate Nash equilibria from leaf to root.
- **Challenges**: Scalability issues due to global payoff dependencies.
- **Future Directions**: Simplified models to improve performance.

### 4. **Mechanism Design**
- **Objective**: Incentivize truthful utility declarations for selecting the maximum weighted path between \( s \) and \( t \).
- **Implementation**: A VCG mechanism ensures that truthfully reporting utility is the dominant strategy.
- **Results**:
  - Players gain the most by declaring their true utility in single-play settings.

![Mechanism Design Results](path/to/mechanism_design_plot.png)
*Figure 5: Gain of a player under truthful reporting.*

## Technical Details
- **Languages & Tools**:
  - Python (used for computation and benchmarking).
  - Google Colab (environment for running experiments).
  - `time` module (for performance evaluation).
- **Graph Categories**:
  - Sparse graphs: Edge density in [0.1, 0.5].
  - Dense graphs: Edge density in [0.5, 0.9].
- **Experiments**:
  - Benchmarked naive and optimized approaches for Shapley Value and Nash Equilibria computation.

## Results Summary
### Shapley Value Computation (Average Time in Seconds)
| Approach  | Sparse Graphs | Dense Graphs |
|-----------|---------------|--------------|
| Naive     | 12.67         | 14.79        |
| Optimized | 1.48          | 2.06         |

### Nash Equilibria Computation (Average Time in Seconds)
| Approach  | Sparse Graphs | Dense Graphs |
|-----------|---------------|--------------|
| Naive     | 0.60          | 0.23         |
| Optimized | 0.16          | 0.18         |
