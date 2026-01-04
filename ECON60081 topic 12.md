---
ContentType: " handwritten"
date: 2026-01-04
tags:
  - topic/math
modified: false
aliases:
---
# ECON 60081: Topic 12 - Differential Equations

## 1. First-Order Linear Equations

A first-order linear differential equation has the standard form:

$$\dot{x} + a(t)x = b(t)$$

### Solution Method: Integrating Factor

To solve this, we introduce an integrating factor $e^{A(t)}$. We define $A(t)$ such that its derivative equals $a(t)$:

$$\frac{dA(t)}{dt} = a(t) \implies A(t) = \int a(t) dt$$

Multiplying the original equation by $e^{A(t)}$ allows us to rewrite the left side as a total derivative:

$$\frac{d}{dt} (x e^{A(t)}) = \dot{x} e^{A(t)} + x e^{A(t)} a(t) = b(t) e^{A(t)}$$

### General Solution

By integrating both sides with respect to $t$, we obtain the general solution:

$$x(t) = C e^{-\int a(t)dt} + e^{-\int a(t)dt} \int b(t) e^{\int a(t)dt} dt$$

Where $C$ is a constant of integration determined by initial conditions.

## 2. Bernoulli Equation

The Bernoulli equation is a specific type of non-linear equation that can be linearized:

$$\dot{x} + a(t)x = b(t)x^{r}$$

### Transformation Steps

1. Divide by $x^r$:
    
    $$x^{-r}\dot{x} + a(t)x^{1-r} = b(t)$$
2. Change of Variables:
    
    Let $z = x^{1-r}$. Then, calculating the derivative of $z$ with respect to $t$:
    
    $$\frac{dz}{dt} = (1-r)x^{-r}\dot{x} \implies x^{-r}\dot{x} = \frac{1}{1-r} \dot{z}$$
3. Linearized Form:
    
    Substituting back into the equation:
    
    $$\frac{1}{1-r}\dot{z} + a(t)z = b(t)$$
    
    Multiplying by $(1-r)$:
    
    $$\dot{z} + (1-r)a(t)z = (1-r)b(t)$$
    
    This is now a first-order linear equation in terms of $z$.
    

## 3. Autonomous Equations

An autonomous equation is one where the rate of change depends only on the state $x$, not explicitly on time $t$:

$$\dot{x} = F(x)$$

### Equilibrium and Stability

An equilibrium point $x^*$ occurs where the rate of change is zero:

$$F(x^*) = 0 \implies x = x^* \text{ is a constant solution.}$$

To determine the stability of an equilibrium $x^*$, we examine $F'(x^*)$:

1. Locally Asymptotically Stable:
    
    If $F'(x^*) < 0$:
    
    - For $x < x^*$, $\dot{x} = F(x) > 0$ (state increases towards $x^*$).
        
    - For $x > x^*$, $\dot{x} = F(x) < 0$ (state decreases towards $x^*$).
        
    - Conclusion: $x(t) \to x^*$ as $t \to \infty$.
        
2. Unstable:
    
    If $F'(x^*) > 0$:
    
    - The state moves away from $x^*$ if perturbed.
        

### Properties of Solutions

- **Monotonicity**: Since $F(x)$ is continuous and differentiable, every solution is either constant (at equilibrium) or strictly monotonic (increasing or decreasing).
    
- **Convergence**: If a solution is bounded and approaches a limit, that limit must be an equilibrium state: $\lim_{t\to\infty} x(t) = x^*$, where $F(x^*) = 0$.
    

## 4. Local Existence and Uniqueness

If $F$ is **continuously differentiable** ($C^1$) in an open neighborhood $B$ of a point $(t_0, x_0)$:

- **Existence**: There exists at least one local solution $x(t)$ passing through $(t_0, x_0)$.
    
- **Uniqueness**: There exists **exactly one** such solution.

