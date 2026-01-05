---
ContentType: " handwritten"
date: 2026-01-05
tags:
  - topic/econ/emet
modified: false
aliases:
  - large sample analysis
---
# ECON61001: Large Sample Analysis (Week 5)

This document provides a structured digitization of the handwritten notes covering Large Sample Analysis in Econometrics, focusing on OLS properties, limit theorems, and asymptotic inference.

## 5-4: Introduction to Large Sample Analysis

### 1. Normal Equations and Sample Representation

Starting with the standard OLS framework, the estimate $\hat{\beta}$ can be expressed as:

$$\hat{\beta} = \beta_0 + (X'X)^{-1}X'u$$

In a sample context (time series or cross-section), this is reflected as:

$$\hat{\beta}_T = \beta_0 + \left( \sum_{t=1}^{T} X_t X_t' \right)^{-1} \sum_{t=1}^{T} X_t u_t$$

We are interested in how statistics of interest (e.g., $t$-stats) behave as the sample size $T \to \infty$.

### 2. Key Concepts of Convergence

#### A. Convergence in Probability (plim)

A random variable $V_T$ converges in probability to $V$ (denoted $V_T \xrightarrow{p} V$) if:

$$P(|V_T - V| > \epsilon) \to 0 \quad \text{for any } \epsilon > 0 \text{ as } T \to \infty$$

- If $V$ is a degenerate random variable (a constant $c$), then $c$ is the **probability limit** of $V_T$: $\text{plim } V_T = c$.
    
- $V_T$ is then called a **consistent** estimator of $c$.
    
- For a matrix $M_T$, $M_T \xrightarrow{p} M$ if and only if every element $m_{ij,T} \xrightarrow{p} m_{ij}$.
    

Slutsky's Theorem:

If $U_T \xrightarrow{p} V$ and $g(\cdot)$ is a continuous function, then:

$$g(U_T) \xrightarrow{p} g(V)$$

_(Note: This applies to probability limits as well: if_ $\text{plim } U_T = \alpha$_, then_ $\text{plim } g(U_T) = g(\alpha)$_)_.

#### B. Convergence in Distribution

Let $\{U_T\}$ be a sequence of random variables with distribution functions $\{F_T(\cdot)\}$. $U_T$ converges in distribution to $V$ (denoted $U_T \xrightarrow{d} V$) if:

$$F_T(c) \to F(c) \text{ as } T \to \infty$$

at all points $c$ where $F(\cdot)$ is continuous. $F$ is called the **limiting distribution**.

## 5-5: Fundamental Limit Theorems

To analyze $\hat{\beta}_T = \beta_0 + \left( \frac{1}{T} \sum X_t X_t' \right)^{-1} \left( \frac{1}{T} \sum X_t u_t \right)$, we use two core theorems:

### 1. Weak Law of Large Numbers (WLLN)

For random vectors $\{V_t\}$ with $E[V_t] = \mu_t$:

$$\frac{1}{T} \sum_{t=1}^{T} (V_t - \mu_t) \xrightarrow{p} 0$$

### 2. Central Limit Theorem (CLT)

Under general conditions:

$$T^{-1/2} \sum_{t=1}^{T} (V_t - \mu_t) \xrightarrow{d} N(0, \Omega)$$

Where $\Omega$ is the positive semi-definite (p.s.d.) matrix of constants:

$$\Omega = \lim_{T \to \infty} \text{Var}\left[ T^{-1/2} \sum_{t=1}^{T} (V_t - \mu_t) \right]$$

### 3. Useful Results for Large Samples

- **Product Rule:** If $\alpha_T = M_T w_T$, where $\text{plim } M_T = M$ and $w_T \xrightarrow{d} N(0, \Sigma)$, then:
    
    $$\alpha_T \xrightarrow{d} N(0, M \Sigma M')$$
- **Quadratic Forms:** If $w_T \xrightarrow{d} N(0, \Omega)$ and $\Omega$ is positive definite (p.d.), then:
    
    $$w_T' \Omega^{-1} w_T \xrightarrow{d} \chi_q^2 \quad \text{where } q = \text{rank}(\Omega)$$

## 5-6: Large Sample Properties of OLS (Cross-Section)

Data setup: $\{(y_i, x_i')\}_{i=1}^N$ is $i.i.d.$

Assumptions: $E[x_i x_i'] = Q$ (finite and positive definite).

### 1. Consistency

The OLS estimator is:

$$\hat{\beta}_N = \beta_0 + \left( N^{-1} \sum_{i=1}^{N} x_i x_i' \right)^{-1} \left( N^{-1} \sum_{i=1}^{N} x_i u_i \right)$$

- By WLLN: $N^{-1} \sum x_i x_i' \xrightarrow{p} Q$ (non-singular).
    
- By WLLN: $N^{-1} \sum x_i u_i \xrightarrow{p} E[x_i u_i]$.
    
    Using the Law of Iterated Expectations (LIE), we show $E[x_i u_i] = 0$:
    
    $$E[x_i u_i] = E[E[x_i u_i | x_i]] = E[x_i E[u_i | x_i]]$$
    
    Given the assumption $E[u_i | x_i] = 0$ (orthogonal condition), it follows that:
    
    $$E[x_i \cdot 0] = 0$$
- By Slutsky's Theorem: $\hat{\beta}_N - \beta_0 \xrightarrow{p} Q^{-1} \cdot 0 = 0$.
    
    Thus, $\hat{\beta}_N \xrightarrow{p} \beta_0$ (Consistency).
    

### 2. Asymptotic Normality

Rewriting the error term for CLT application:

$$\sqrt{N}(\hat{\beta}_N - \beta_0) = \left( N^{-1} \sum_{i=1}^{N} x_i x_i' \right)^{-1} \left( N^{-1/2} \sum_{i=1}^{N} x_i u_i \right)$$

- The first part converges to $Q^{-1}$ by WLLN.
    
- The second part converges to $N(0, \Omega)$ by CLT.
    
    The derivation for Asymptotic Variance $\Omega$ is as follows:
    
    $$\begin{aligned} \Omega &= \lim_{N \to \infty} \text{Var}\left[ N^{-1/2} \sum_{i=1}^{N} x_i u_i \right] \\ &= \lim_{N \to \infty} N^{-1} \text{Var}\left[ \sum_{i=1}^{N} x_i u_i \right] \\ &= \lim_{N \to \infty} N^{-1} \sum_{i=1}^{N} \text{Var}[x_i u_i] \quad (\text{due to } i.i.d. \text{ assumption}) \\ &= \text{Var}[x_i u_i] = E[x_i u_i u_i' x_i'] - E[x_i u_i]E[x_i u_i]' \\ &= E[u_i^2 x_i x_i'] \quad (\text{since } E[x_i u_i] = 0) \end{aligned}$$
    
    Applying the **Law of Iterated Expectations (LIE)** again:
    
    $$E[u_i^2 x_i x_i'] = E[E[u_i^2 | x_i] x_i x_i']$$
    
    Under **homoskedasticity**, we assume $E[u_i^2 | x_i] = \sigma_0^2$ (a constant):
    
    $$\Omega = E[\sigma_0^2 x_i x_i'] = \sigma_0^2 E[x_i x_i'] = \sigma_0^2 Q$$

Resulting Distribution:

$$\sqrt{N}(\hat{\beta}_N - \beta_0) \xrightarrow{d} N(0, \sigma_0^2 Q^{-1})$$

## 5-7: Asymptotic Inference

### 1. Variance Estimation

According to the notes, to perform inference, we need the estimated variance:

$$\Omega_N = \hat{\sigma}_N^2 N^{-1} X' X$$

The estimated variance of the OLS estimator is:

$$\hat{V}_N = \hat{\sigma}_N^2 (X' X)^{-1} = N^{-1} \hat{\sigma}_N^2 (N^{-1} X' X)^{-1}$$

### 2. t-statistics

Strictly following the handwritten notes, the asymptotic $t$-statistic for $\beta_j$ is:

$$t\text{-stat} = \frac{N^{1/2}(\hat{\beta}_{N, j} - \beta_j)}{\hat{\sigma}_N \sqrt{\hat{q}_{N, jj}^{(-1)}}} \xrightarrow{d} N(0, 1)$$

The notes also provide the matrix-form representation:

$$t\text{-stat} = \left[ \hat{\sigma}_N \sqrt{\hat{q}_{N, jj}^{(-1)}} \right]^{-1} \cdot N^{1/2}(\hat{\beta}_{N, j} - \beta_j)$$

Where $\hat{q}_{N, jj}^{(-1)}$ is the $j$-th diagonal element of $(N^{-1} X' X)^{-1}$.

### 3. Confidence Intervals

Following the structure derived from the $t$-statistic on page 4, an approximate $(1-\alpha)\%$ confidence interval for $\beta_j$ is given by:

$$\hat{\beta}_{N, j} \pm z_{1-\alpha/2} \cdot \hat{\sigma}_N \sqrt{\left( X'X \right)^{-1}_{jj}}$$

To align with the asymptotic notation used in the $t$-statistic ($\hat{q}_{N, jj}^{(-1)}$ and $N^{1/2}$), this can be explicitly decomposed as:

$$\hat{\beta}_{N, j} \pm z_{1-\alpha/2} \cdot \left( \hat{\sigma}_N \cdot \frac{\sqrt{\hat{q}_{N, jj}^{(-1)}}}{N^{1/2}} \right)$$

Where:

- $\hat{\beta}_{N, j}$ is the OLS estimator (point estimate).
    
- $z_{1-\alpha/2}$ is the critical value from the standard normal distribution.
    
- $\hat{\sigma}_N$ is the estimated standard deviation of the error term.
    
- $\sqrt{\left( X'X \right)^{-1}_{jj}}$ (or $\frac{\sqrt{\hat{q}_{N, jj}^{(-1)}}}{N^{1/2}}$) is the square root of the $j$-th diagonal element of the inverse covariance matrix.
    

### 4. Hypothesis Testing (Wald Test)

For linear restrictions $H_0: R\beta_0 = r$:

$$W_N = N(R\hat{\beta}_N - r)' [R (N^{-1} X'X)^{-1} R']^{-1} (R\hat{\beta}_N - r) / \hat{\sigma}_N^2 \xrightarrow{d} \chi_q^2$$

Under $H_0$, where $q = \text{rank}(R)$.

## 5-8: Non-linear Restrictions

For testing $H_0: g(\beta_0) = 0$ vs $H_1: g(\beta_0) \neq 0$:

Define the Jacobian matrix $G(\beta) = \frac{\partial g(\beta)}{\partial \beta'}$, with $\text{rank}[G(\beta_0)] = n_g$.

### 1. Delta Method

Using a 1st-order Taylor expansion around $\beta_0$:

$$g(\hat{\beta}_N) \approx g(\beta_0) + G(\beta_0)(\hat{\beta}_N - \beta_0)$$

This implies the asymptotic distribution:

$$\sqrt{N} g(\hat{\beta}_N) \xrightarrow{d} N(0, G(\beta_0) V G(\beta_0)')$$

### 2. Wald Statistic for Non-linear Restrictions

$$W_N^{(g)} = N \cdot g(\hat{\beta}_N)' [G(\hat{\beta}_N) (N^{-1} X'X)^{-1} G(\hat{\beta}_N)']^{-1} g(\hat{\beta}_N) / \hat{\sigma}_N^2 \xrightarrow{d} \chi_{n_g}^2$$