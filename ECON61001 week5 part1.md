---
ContentType: " handwritten"
date: 2026-01-05
tags:
  - topic/econ/emet
modified: false
aliases:
  - intro to causal inference and DiD
---
# ECON 61001: Causal Inference & Difference-in-Differences (DiD)

## 1. Introduction to Causal Inference

Causal inference aims to determine the effect of a specific treatment or intervention on an outcome of interest.

### 1.1 Basic Components

- **Treatment Group (**$D_i = 1$**):** The group that receives the intervention.
    
- **Control Group (**$D_i = 0$**):** The group that does not receive the intervention.
    
- **Sample Selection:** The process of choosing individuals for the treatment and control groups.
    

### 1.2 The Simple Regression Model

A basic model to estimate the effect is:

$$y_i = \beta_0 + \beta_1 D_i + \epsilon_i$$

Where the naive estimator $\hat{\beta}_1$ is calculated as the difference in sample means:

$$\hat{\beta}_1 = \bar{y}_{Treatment} - \bar{y}_{Control}$$

## 2. Potential Outcomes Framework

The Potential Outcomes Framework (Rubin Causal Model) defines causality by comparing what happened to what _would have_ happened under different conditions.

### 2.1 Individual Treatment Effect

For each individual $i$, the potential outcomes are:

- $Y_{1,i}$: Outcome if treated ($D_i = 1$).
    
- $Y_{0,i}$: Outcome if not treated ($D_i = 0$).
    

The individual treatment effect is defined as:

$$\text{Effect}_i = Y_{1,i} - Y_{0,i}$$

> **Note:** We can never simultaneously observe $Y_{1,i}$ and $Y_{0,i}$ for the same individual at the same time. This is known as the **Fundamental Problem of Causal Inference**.

### 2.2 Aggregate Treatment Effects

- Average Treatment Effect (ATE):
    
    $$ATE = E[Y_{1,i} - Y_{0,i}]$$
- Average Treatment Effect on the Treated (ATET/ATT):
    
    $$ATET = E[Y_{1,i} - Y_{0,i} | D_i = 1]$$

### 2.3 Selection Bias

The observed difference in means can be decomposed into the true effect and selection bias:

$$\Delta = E[Y_i | D_i = 1] - E[Y_i | D_i = 0]$$$$\Delta = ATET + \underbrace{\{ E[Y_{0,i} | D_i = 1] - E[Y_{0,i} | D_i = 0] \}}_{\text{Selection Bias}}$$

- **Selection Bias:** The difference in baseline outcomes ($Y_0$) between the treatment and control groups.
    
- If **Random Assignment** is used, we assume **Unconditional Independence (UI)**, meaning $D_i$ is independent of $(Y_{1,i}, Y_{0,i})$.
    
- Under UI, Selection Bias = 0, and the observed difference $\Delta$ equals the causal effect.
    

## 3. Difference-in-Differences (DiD)

When random assignment is not possible, we often use **Natural Experiments** and the DiD method. A classic example is the study by **Card & Krueger (1994)** on minimum wage.

### 3.1 The DiD Model

Consider two groups (e.g., NJ as Treatment, PA as Control) and two time periods (Before and After policy).

The regression specification is:

$$Y_{i,t} = \beta_0 + \beta_1 D_{Group} + \beta_2 D_{Time} + \beta_3 (D_{Group} \times D_{Time}) + \epsilon_{i,t}$$

Where:

- $D_{Group} = 1$ if Treatment Group (NJ), $0$ otherwise.
    
- $D_{Time} = 1$ if After Period, $0$ otherwise.
    

### 3.2 Decomposition of Coefficients

|   |   |   |   |
|---|---|---|---|
|**Condition**|**Group**|**Period**|**Expected Value**|
|(1)|Treatment|After|$\beta_0 + \beta_1 + \beta_2 + \beta_3$|
|(2)|Treatment|Before|$\beta_0 + \beta_1$|
|(3)|Control|After|$\beta_0 + \beta_2$|
|(4)|Control|Before|$\beta_0$|

**Calculating the Causal Effect:**

1. **Difference in Treatment Group:** $(1) - (2) = \beta_2 + \beta_3$ (Time effect + Policy effect)
    
2. **Difference in Control Group:** $(3) - (4) = \beta_2$ (Pure time effect)
    
3. **Difference-in-Differences:** $[(1) - (2)] - [(3) - (4)] = \beta_3$  
    

Thus, $\beta_3$ identifies the **Causal Effect**.

### 3.3 Key Assumption: Common Trends

The validity of DiD relies on the Common Trends Assumption:

In the absence of the treatment, the difference between the treatment and control groups would have remained constant over time.

Mathematically:

$$E[Y_{0,i, \text{After}} - Y_{0,i, \text{Before}} | D_i=1] = E[Y_{0,i, \text{After}} - Y_{0,i, \text{Before}} | D_i=0]$$