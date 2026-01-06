---
ContentType: " handwritten"
date: 2026-01-06
tags:
  - topic/math
modified: false
aliases:
  - second order differential equations
---
# Topic 13: Second Order Differential Equations

This document summarizes the theory, solution methods, and stability analysis of second-order differential equations based on the lecture notes.

## 1. Introduction to Second Order Differential Equations

A general second-order differential equation can be expressed as:

$$x'' = f(t, x, x')$$

### 1.1 Methods of Solution

1. Reduction to First Order:
    
    If the equation can be simplified, we define a new variable:
    
    $$\text{Let } u = x' \Rightarrow u' = f(t, u)$$
    
    This reduces the problem to a system of first-order equations.
    
2. 2nd Order Linear Equations:
    
    The standard form is:
    
    $$x'' + a(t)x' + b(t)x = f(t)$$

## 2. Homogeneous Linear Equations

Consider the homogeneous case where $f(t) = 0$:

$$x'' + a(t)x' + b(t)x = 0$$

### 2.1 General Properties

- **Linear Combination:** If $u$ and $v$ are two solutions, then $x(t) = Au + Bv$ is also a solution.
    
- General Solution: If $u$ and $v$ are linearly independent (not proportional), then the general solution is:
    
    $$x_h(t) = Au + Bv$$

### 2.2 Constant Coefficients Case

For the equation $x'' + ax' + bx = 0$, we try the solution $x = e^{rt}$. Substituting this into the equation yields the characteristic equation:

$$r^2 + ar + b = 0$$

The roots are given by:

$$r_{1,2} = \frac{-a \pm \sqrt{a^2 - 4b}}{2}$$

#### Case Analysis:

|   |   |   |
|---|---|---|
|**Discriminant (a2−4b)**|**Root Type**|**General Solution xh​(t)**|
|$a^2 - 4b > 0$|Distinct Real Roots ($r_1, r_2$)|$x(t) = Ae^{r_1 t} + Be^{r_2 t}$|
|$a^2 - 4b = 0$|Repeated Real Root ($r = -a/2$)|$x(t) = (A + Bt)e^{-\frac{a}{2}t}$|
|$a^2 - 4b < 0$|Complex Roots ($\alpha \pm i\beta$)|$x(t) = e^{\alpha t}(A \cos \beta t + B \sin \beta t)$|

_Where_ $\alpha = -a/2$ _and_ $\beta = \sqrt{b - a^2/4}$_._

## 3. Non-Homogeneous Equations: Method of Undetermined Coefficients

For the equation $x'' + ax' + bx = f(t)$, the general solution is:

$$x(t) = x_h(t) + x_p(t)$$

Where $x_p(t)$ is a particular solution.

### 3.1 Choosing the Form of $x_p(t)$  

The trial solution $x_p(t)$ depends on the form of $f(t)$:

1. Polynomial $f(t)$:
    
    If $f(t)$ is a polynomial of degree $n$, try $x_p(t)$ as a polynomial of the same degree.
    
2. Exponential $f(t) = Pe^{qt}$:
    
    Try $x_p(t) = Ce^{qt}$. Substituting into the equation:
    
    $$Ce^{qt}(q^2 + aq + b) = Pe^{qt} \Rightarrow C = \frac{P}{q^2 + aq + b}$$
    
    Note: This works if $q$ is not a root of the characteristic equation ($q^2 + aq + b \neq 0$).
    
3. Adjustment for Homogeneous Solutions:
    
    If $f(t)$ is already a solution to the homogeneous equation:
    
    - If $q$ is a simple root: Try $x_p(t) = Cte^{qt}$.
        
    - If $q$ is a repeated root: Try $x_p(t) = Ct^2e^{qt}$.
        
4. Trigonometric $f(t) = p \sin rt + q \cos rt$:
    
    Try $x_p(t) = A \sin rt + B \cos rt$.
    
    If this form is part of $x_h(t)$, try $x_p(t) = t(A \sin rt + B \cos rt)$.
    

## 4. Euler's Differential Equation

The general form of Euler's equation is:

$$t^2 x'' + atx' + bx = 0, \quad t > 0$$

### 4.1 Solution Method

Try $x = t^r$. Then $x' = rt^{r-1}$ and $x'' = r(r-1)t^{r-2}$. Substituting these into the equation:

$$r(r-1)t^r + art^r + bt^r = 0$$

Dividing by $t^r$ gives the auxiliary equation:

$$r^2 + (a-1)r + b = 0$$

#### Solution Cases:

- Distinct Real Roots ($r_1 \neq r_2$):
    
    $$x(t) = At^{r_1} + Bt^{r_2}$$
- Repeated Real Roots ($r_1 = r_2$):
    
    $$x(t) = (A + B \ln t)t^r$$
- Complex Roots ($\alpha \pm i\beta$):
    
    $$x(t) = t^\alpha [A \cos(\beta \ln t) + B \sin(\beta \ln t)]$$
    
    Where $\alpha = \frac{1-a}{2}$ and $\beta = \frac{1}{2}\sqrt{4b - (a-1)^2}$.
    

## 5. Stability of Linear Differential Equations

Consider the non-homogeneous equation $x'' + ax' + bx = f(t)$. Let $x(t)$ be the general solution and $y(t)$ be a particular solution.

### 5.1 Global Asymptotic Stability

The solution is globally asymptotically stable if:

$$\lim_{t \to \infty} [x(t) - y(t)] = 0$$

### 5.2 Necessary and Sufficient Conditions

A second-order linear differential equation with constant coefficients is globally asymptotically stable if and only if all roots of the characteristic polynomial $r^2 + ar + b$ have **negative real parts**.

According to **Vieta's Formulas** for $r^2 + ar + b = 0$:

1. $r_1 + r_2 = -a$  
    
2. $r_1 \cdot r_2 = b$  
    

Stability Condition:

$$\text{Stability} \iff a > 0 \text{ and } b > 0$$

_End of Notes_