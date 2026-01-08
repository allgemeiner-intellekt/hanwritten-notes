---
ContentType: " handwritten"
date: 2026-01-08
tags:
  - topic/econ
modified: false
aliases:
---
# ECON60101: General Equilibrium Theory

## 1. Equilibrium and Efficiency (GE-1)

This section explores the relationship between Walrasian Equilibrium (WE) allocations and Pareto Efficiency (PE).

### 1.1 The First Fundamental Welfare Theorem (FWT)

- **Statement:** Any Walrasian Equilibrium allocation is Pareto Efficient.
    
- **Implication:** Under certain conditions, competitive markets lead to an efficient allocation of resources.
    
- **Limitation:** The FWT says nothing about the **distribution** of economic benefits. An allocation can be efficient but highly unequal.
    

### 1.2 Informational Efficiency

The market mechanism is efficient in terms of information handling:

- **Preference and Endowment:** Consumers only need to know their own preferences and endowments.
    
- **Price Decision:** The price acts as a sufficient statistic for making decisions, leading to "information saving."
    

### 1.3 The Second Fundamental Welfare Theorem (SWT)

- **Concept (The Converse):** Given a Pareto Efficient allocation, can we find a price vector $p$ such that the allocation is a Walrasian Equilibrium?
    
- **Intuition:**
    
    - A Pareto Efficient allocation implies that indifference curves are tangent.
        
    - The slope of the tangent line at the PE allocation represents the **relative price**.
        
- **Conditions:** Requires **convex preferences**.
    
- **Implementation:**
    
    - To reach a specific PE allocation that is considered "fair," the government/social planner can **reallocate initial endowments**.
        
    - Once endowments are redistributed, the budget constraint aligns with the tangent line, and the market naturally reaches the desired WE.
        
- **Separability Principle:** Efficiency is achieved by markets (which are distributionally neutral), while equity is achieved through the reallocation of initial endowments.
    

## 2. Mathematical Foundation and the Role of Prices (GE-7)

### 2.1 Dual Role of Prices

1. **Allocative Role:** Prices signal scarcity and guide the allocation of resources.
    
2. **Distributive Role:** Prices determine the wealth of agents based on their endowments.
    

### 2.2 Proof of SWT: Separating Hyperplane Theorem

The formal proof of the Second Welfare Theorem relies on the **Separating Hyperplane Theorem**:

- **Theorem:** Two non-overlapping convex sets can be separated by a hyperplane.
    
- In the context of GE, these sets are the aggregate preferred set and the aggregate production/endowment set. The price vector $p$ defines the normal to this separating hyperplane.
    

## 3. General Equilibrium with Production (GE-8)

### 3.1 The Firm and Production

The production sector consists of firms $j = 1, \dots, J$, each defined by a **Production Possibility Set** $Y^j$.

**Assumptions on** $Y^j$**:**

1. $0 \in Y^j \subseteq \mathbb{R}^N$ (Possibility of inaction).
    
2. $Y^j$ is **compact** (closed and bounded).
    
3. $Y^j$ is **strongly convex**, which implies **decreasing returns to scale (DRS)**.
    

**Firm's Behavior:**

- A production plan is denoted as $y^j \in Y^j$, where negative components are inputs and positive components are outputs.
    
- **Profit Maximization Problem:** $\max p \cdot y^j$ s.t. $y^j \in Y^j$.
    
- **Profit Function:** $\Pi^j(p) \equiv \max_{y^j \in Y^j} p \cdot y^j$.
    

### 3.2 The Consumer with Production

In addition to the standard pure exchange assumptions:

- **Profit Sharing:** Consumers own shares of firms. Let $0 \le \theta^{ij} \le 1$ be the share of firm $j$ owned by consumer $i$, such that $\sum_{i=1}^I \theta^{ij} = 1$ for all $j$.
    
- **Income (**$m^i$**):** $m^i(p) = p \cdot e^i + \sum_{j=1}^J \theta^{ij} \Pi^j(p)$.
    
- Utility Maximization Problem:
    
    $$\max u_i(x^i) \quad \text{s.t.} \quad x^i \in B^i(p) \equiv \{ x^i \in \mathbb{R}_+^L : p \cdot x^i \le m^i(p) \}$$

### 3.3 Aggregate Excess Demand

The key to equilibrium is the **Aggregate Excess Demand Function** $Z(p)$.

- For market $k$:
    
    $$Z_k(p) = \sum_{i=1}^I x_k^i(p, m^i(p)) - \sum_{j=1}^J y_k^j(p) - \sum_{i=1}^I e_k^i$$
- **Equilibrium Condition:** Find $p^*$ such that $Z(p^*) = 0$.
    

## 4. Welfare and Existence Theorems (GE-9)

### 4.1 Welfare Theorems with Production

- **FWT with Production:** Any Walrasian Equilibrium allocation in an economy with production is Pareto Efficient.
    
- **SWT with Production:** Given assumptions on $Y^j$ (convexity), any PE allocation can be supported as a WE after appropriate income transfers.
    

### 4.2 Non-Existence of Equilibrium (Counter-examples)

Equilibrium might fail to exist if:

1. **Preferences are non-convex:**
    
    - e.g., $u_1(x, y) = \min\{x, y\}$ (Leontief) and $u_2(x, y) = \max\{x, y\}$ (Concave/Non-convex).
        
2. **Endowments are not strictly positive:**
    
    - e.g., $e_1 = (10, 0)$ and $e_2 = (0, 10)$.
        

### 4.3 Sonnenschein-Mantel-Debreu (SMD) Theorem

The SMD theorem addresses the constraints that individual rationality imposes on aggregate behavior.

- **Properties of Aggregate Excess Demand (**$Z(p)$**):**
    
    1. Continuity.
        
    2. Homogeneity of degree zero in prices.
        
    3. **Walras' Law:** $p \cdot Z(p) = 0$.
        
- **Theorem:** These three properties are the _only_ properties that an aggregate excess demand function must satisfy. Any function satisfying these can be generated by an economy with rational consumers (with utility-maximizing preferences and initial endowments).
    
- **Conclusion:** Utility maximization imposes no extra conditions on aggregate behavior beyond these three properties.
    

### 4.4 Brown-Matzkin Theorem

- This theorem concerns the observability of preferences.
    
- Given observations of prices and endowments, it asks whether we can infer if the data is consistent with GE theory, even if preferences are not strictly monotone.