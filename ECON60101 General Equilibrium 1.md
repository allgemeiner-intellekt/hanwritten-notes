---
ContentType: " handwritten"
date: 2026-01-05
tags:
  - topic/econ
modified: false
aliases:
---
# General Equilibrium I: Exchange Economy

This document provides a structured summary of the lecture notes on General Equilibrium (GE), focusing on the pure exchange economy, Pareto efficiency, the Core, and Walrasian equilibrium.

## 1. Basic Definitions

In a pure exchange economy, we focus on the allocation of existing goods among agents without production.

- **Consumption Bundle**: For agent $i$, the consumption bundle is represented as $x^i = (x^1_i, \dots, x^N_i) \in \mathbb{R}^N_+$.
    
- **Allocation**: A vector of consumption bundles for all agents: $x = (x^1, \dots, x^I)$.
    
- **Endowment**: The initial resource holdings of agents: $e = (e^1, \dots, e^I)$.
    
- **Utility Function**: Each agent $i$ has a utility function $u^i(x^i)$ representing their preferences.
    

### Feasible Allocations

An allocation $x$ is feasible in a pure exchange economy if the total consumption of each good $j$ does not exceed the total endowment:

$$F(e) = \left\{ x \in \mathbb{R}^{IN}_+ : \sum_{i=1}^I x^i_j = \sum_{i=1}^I e^i_j, \forall j = 1, \dots, N \right\}$$

Note: For any commodity, the total supply is fixed by the aggregate endowment.

## 2. The $2 \times 2$ Economy and Edgeworth Box

To simplify the analysis of bilateral exchange, we use the **Edgeworth Box**.

- **Dimensions**: The height and width of the box represent the total endowment of the two commodities.
    
- Feasibility: Any point within the box represents a feasible allocation where:
    
    $$x^1_j + x^2_j = e^1_j + e^2_j$$
- **Mechanism**: Agents trade from an initial endowment point until all possibilities for mutually beneficial trade are exhausted. Such an allocation is deemed **Pareto Efficient**.
    

## 3. Pareto Efficiency

An allocation $z \in F(e)$ is **Pareto Efficient** if there is no other feasible allocation $\hat{z} \in F(e)$ such that:

1. $u^i(\hat{z}^i) \ge u^i(z^i)$ for all agents $i$.
    
2. $u^i(\hat{z}^i) > u^i(z^i)$ for at least one agent $i$.
    

Geometrical Interpretation:

In an Edgeworth Box, Pareto efficient points occur where the indifference curves of the two agents are tangent to each other. This implies that their Marginal Rates of Substitution (MRS) are equal:

$$MRS^1_{1,2} = MRS^2_{1,2}$$

## 4. The Pareto Set and the Core

### Pareto Set (Contract Curve)

The collection of all Pareto efficient allocations is called the **Pareto Set** or the **Contract Curve**.

### The Core

Starting from a specific initial endowment, agents will only agree to trades that make them no worse off. The **Core** consists of the subset of Pareto efficient allocations that are "unblocked" by any individual or coalition.

- **Blocking Coalition**: A set of agents $S$ blocks an allocation $x$ if they can find a feasible allocation $y$ using only their own endowments ($\sum_{i \in S} y^i = \sum_{i \in S} e^i$) such that everyone in $S$ is at least as well off and someone is strictly better off.
    
- **Definition**: The Core is the set of feasible allocations that cannot be blocked by any coalition.
    
    - For bilateral exchange, the Core is the segment of the Contract Curve that lies between the two agents' initial indifference curves.
        

## 5. Competitive Markets and Walrasian Equilibrium

In competitive markets, agents act as price-takers.

- **Initial Income**: $y^i(p) = \sum_{j=1}^N p_j e^j_j = p \cdot e^i$.
    
- **Budget Set**: $B^i(p) = \{ x^i \in \mathbb{R}^N_+ : p \cdot x^i \le y^i(p) \}$.
    
- **Walrasian Demand**: $x^i(p, y^i(p))$ is the bundle that maximizes $u^i$ subject to the budget constraint.
    

### Walrasian Equilibrium (WE)

A price vector $p^*$ and an allocation $x^*$ constitute a Walrasian Equilibrium if:

1. Each agent chooses their most preferred affordable bundle.
    
2. Markets clear (Total excess demand is zero):
    
    $$Z_j(p) = \sum_{i=1}^I x^i_j(p) - \sum_{i=1}^I e^i_j = 0, \forall j$$

### Walras' Law

If $N-1$ markets clear, the $N$-th market must also clear. This follows from the aggregate budget constraint:

$$\sum_{j=1}^N p_j Z_j(p) = 0$$

Geometrical Interpretation:

A Walrasian Equilibrium occurs at the intersection of the agents' Offer Curves in the Edgeworth Box.

## 6. Existence and Properties of Equilibrium

### Conditions for Existence

The existence of $p^*$ such that $Z(p^*) = 0$ is guaranteed if the aggregate excess demand function $Z(p)$ satisfies certain properties:

1. **Continuity**: Derived from the continuity of utility functions and the maximum theorem.
    
2. **Homogeneity of Degree Zero**: $Z(\lambda p) = Z(p)$ for $\lambda > 0$. Only relative prices matter.
    
3. **Walras' Law**: $p \cdot Z(p) = 0$.
    

### Fundamental Assumptions

- $u^i(\cdot)$ is continuous, strictly increasing (monotonicity), and quasi-concave.
    
- Initial endowments are strictly positive: $e^i \gg 0$.
    

### Uniqueness and Efficiency

- **Uniqueness**: A Walrasian Equilibrium is not necessarily unique (multiple equilibria are possible but usually finite).
    
- **Core and WE**: Any Walrasian Equilibrium allocation belongs to the Core. Since $p$ is the same for all agents, $MRS^i = p_1/p_2$ for all $i$, ensuring Pareto efficiency.
    

_End of Notes_