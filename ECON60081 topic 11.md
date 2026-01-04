---
ContentType: " handwritten"
date: 2026-01-04
tags:
  - topic/math
modified: false
aliases:
---
# ECON60081 Topic 11: Differential Equations

## 1. Overview and Definitions

In differential equations, the **unknown** is a function, and the equation includes the **derivatives** of this unknown function.

- **Geometric Representation:**
    
    - The graph of a solution is referred to as a **solution curve** or an **integral curve**.
        
    - **Slope Field (Direction Diagram):** A graphical representation used to visualize the behavior of solutions by drawing short line segments representing the slope at various points.
        
- **Types of Solutions:**
    
    1. **General Solution:** Contains an arbitrary constant ($C$).
        
    2. **Particular Solution:** Obtained by assigning specific values to the constants (usually based on initial conditions).
        

## 2. Key Solution Methods

### 2.1 Separable Equations

A first-order differential equation is **separable** if it can be written in the form:

$$\dot{x} = f(t)g(x)$$

**Solution Steps:**

1. Rewrite the derivative as $\frac{dx}{dt} = f(t)g(x)$.
    
2. Rearrange the terms to separate variables:
    
    $$\frac{1}{g(x)} dx = f(t) dt$$
3. Integrate both sides (assuming $g(x) \neq 0$):
    
    $$\int \frac{1}{g(x)} dx = \int f(t) dt$$
4. Solve for $x(t)$ to find the explicit solution.
    

Stationary Solutions:

If there exists an $x_0$ such that $g(x_0) = 0$, then $\dot{x}_0 = f(t)g(x_0) = 0$. In this case, $x(t) = x_0$ (a constant) is a stationary solution.

### 2.2 First-Order Linear Equations

The general form of a first-order linear differential equation is:

$$\dot{x} + a(t)x = b(t)$$

#### A. The Simplest Case (Constant Coefficients)

Consider the case where $a$ is a constant and $a \neq 0$:

$$\dot{x} + ax = b$$

**Method: Integrating Factor**

1. Multiply both sides by the integrating factor $e^{at}$:
    
    $$(\dot{x} + ax)e^{at} = be^{at}$$
2. Notice that the left side is the derivative of a product:
    
    $$\frac{d}{dt}(xe^{at}) = be^{at}$$
3. Integrate both sides:
    
    $$xe^{at} = \int be^{at} dt = \frac{b}{a}e^{at} + C$$
4. Solve for $x$:
    
    $$x(t) = \frac{b}{a} + Ce^{-at}$$

**Stability Analysis:**

- **If** $a > 0$**:** As $t \to \infty$, $e^{-at} \to 0$. Thus, $x(t)$ **converges** to $\frac{b}{a}$ (**Stable**).
    
- **If** $a < 0$**:** The term $e^{-at}$ grows indefinitely, and the solution is **Unstable**.
    

#### B. Variable Coefficients

For the general linear equation $\dot{x} + a(t)x = b(t)$, the solution structure is:

$$xe^{a(t)} = \int b(t)e^{a(t)} dt$$

Which simplifies to:

$$x(t) = Ce^{-a(t)} + e^{-a(t)} \int b(t)e^{a(t)} dt$$

