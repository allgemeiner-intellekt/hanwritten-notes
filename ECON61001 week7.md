---
ContentType: " handwritten"
date: 2026-01-09
tags:
  - topic/econ/emet
modified: false
aliases:
---
# ECON61001 Week 7: Large Sample Properties in Time Series

This document summarizes the handwritten lecture notes on large sample theory for time series analysis, focusing on stochastic processes, stationarity, and the asymptotic properties of OLS estimators.

## 1. Introduction to Stochastic Processes

In time series analysis, we often deal with a **large sample** where the sample size $T \to \infty$. A typical model might include lagged dependent variables and exogenous regressors:

$$y_{t} = \beta_{0} + \beta_{1} y_{t-1} + \beta_{2} x_{t} + \beta_{3} x_{t-1} + u_{t}$$

### Key Concepts:

- **Stochastic Process:** A sequence of random variables $\{U_{t}\}_{t=-\infty}^{\infty}$.
    
- **Realization:** A specific observed path of the process.
    
- **Effective Sample Size:** Unlike cross-sectional data where we have $N$ independent draws, in time series, we typically observe only **one realization** of the process over $T$ periods.
    

### Comparison: Cross-Section vs. Time Series

- **Cross-Section:** Observations are typically assumed to be Independent and Identically Distributed (i.i.d.).
    
- **Time Series:** Observations are naturally ordered and often correlated over time, making the standard i.i.d. assumption untenable.
    

## 2. Stationarity and Dependence

To apply the Law of Large Numbers (WLLN) and Central Limit Theorem (CLT) to time series, we need to replace the i.i.d. condition with **Stationarity** and **Weak Dependence**.

### 2.1 Stationarity

Stationarity implies that the joint distribution of the process remains invariant over time.

- Strong (Strict) Stationarity:
    
    The joint distribution of any collection of variables is invariant to time shifts:
    
    $$F(\{V_{t_1}, \dots, V_{t_n}\}) = F(\{V_{t_1+c}, \dots, V_{t_n+c}\})$$
- Weak (Covariance) Stationarity:
    
    A process is weakly stationary if it satisfies three conditions:
    
    1. **Constant Mean:** $E[V_{t}] = \mu$ (independent of $t$).
        
    2. **Constant Variance:** $Var(V_{t}) = \sigma^2 < \infty$ (independent of $t$).
        
    3. **Constant Autocovariance:** $Cov(V_{t}, V_{t-s}) = \gamma_{s}$ (depends only on the lag $s$, not on $t$).
        

### 2.2 Weak Dependence

Weak dependence refers to the "memory" of the process. As the distance between two time periods $s$ increases, the correlation between $V_t$ and $V_{t-s}$ should diminish.

- **Condition:** $Cov(V_t, V_{t-s}) \to 0$ as $s \to \infty$ at a sufficiently fast rate.
    
- **Importance:** This is a sufficient condition for the WLLN and CLT to hold. It is violated by unit root processes but holds for trend-stationary processes.
    

## 3. Asymptotic Normality and Long-Run Variance

Under stationarity and weak dependence:

$$T^{-1/2} \sum_{t=1}^{T} (V_{t} - \mu) \xrightarrow{d} N(0, \Omega)$$

Where $\Omega$ is the Long-Run Variance, defined as the sum of all autocovariances:

$$\Omega = \sum_{j=-\infty}^{\infty} \Gamma_{j} = \Gamma_{0} + \sum_{j=1}^{\infty} (\Gamma_{j} + \Gamma_{j}')$$

Note that $\Gamma_{j} = Cov(V_t, V_{t-j})$.

## 4. Exogeneity and OLS Consistency

In the stochastic regressor model, consistency depends on the relationship between regressors ($X$) and the error term ($u$).

### 4.1 Strict vs. Contemporaneous Exogeneity

- **Strict Exogeneity:** $E[u_{t} | \mathbf{X}] = 0$ for all $t$. This requires the error to be uncorrelated with $x$ in all past, present, and future periods.
    
    - _Note:_ This is often violated in models with lagged dependent variables (e.g., AR(1) models).
        
- **Contemporaneous Exogeneity:** $E[u_{t} | X_{t}] = 0$. This only requires the error to be uncorrelated with the current regressor.
    

### 4.2 The AR(1) Case

Consider $y_{t} = \beta_{0} + \beta_{1} y_{t-1} + u_{t}$.

Since $y_{t-1}$ is a function of $u_{t-1}$, strict exogeneity fails. However, if $E[u_t | y_{t-1}] = 0$, OLS can still be consistent under weak stationarity and weak dependence.

## 5. OLS Assumptions for Time Series (TS1 - TS6)

The standard Gauss-Markov assumptions are adapted for time series:

1. **TS1 (Linearity):** The model is linear in parameters.
    
2. **TS2 (Weak Dependence):** The process is stationary and weakly dependent.
    
3. **TS3 (Contemporaneous Exogeneity):** $E[u_t | X_t] = 0$.
    
4. **TS4 (No Perfect Collinearity):** Regressors are not perfectly correlated.
    
5. **TS5 (Homoskedasticity):** $Var(u_t | X_t) = \sigma^2$.
    
6. **TS6 (No Serial Correlation):** $E[u_t u_s | X_t, X_s] = 0$ for $t \neq s$.
    

### Dynamic Completeness

A model is dynamically complete if it captures all relevant information from the past:

$$E[y_{t} | I_{t-1}] = x_{t}' \beta$$

Where $I_{t-1}$ is the information set at time $t-1$. Dynamic completeness implies TS6 (no serial correlation).

## 6. Inference and Variance Matrix

If assumptions TS1-TS6 hold, the OLS estimator is asymptotically normal. If TS5 or TS6 are violated (**Non-spherical distributions**), we must use Robust Standard Errors or Generalized Least Squares (GLS).

- **Spherical Distribution:** Errors are i.i.d. $\implies Var(u) = \sigma^2 I$.
    
- **Non-spherical Distribution:** Presence of heteroskedasticity or autocorrelation.

