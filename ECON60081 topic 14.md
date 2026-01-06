---
ContentType: " handwritten"
date: 2026-01-06
tags:
  - topic/math
modified: false
aliases:
  - simultaneous differential equations
---
# ECON 60081 Topic 14: Simultaneous Differential Equations (First Order)

## 1. Overview

The primary goal is to solve a system of simultaneous first-order differential equations. There are two main approaches:

1. **Reduction to a single Second-Order Ordinary Differential Equation (ODE).**
    
2. **Linear system analysis using constant coefficients and Matrix methods.**
    

## 2. Linear Systems with Constant Coefficients

Consider a system of two first-order linear differential equations:

$$\begin{aligned} \dot{x} &= a_{11}x + a_{12}y + b_1(t) \\ \dot{y} &= a_{21}x + a_{22}y + b_2(t) \end{aligned}$$

### 2.1 The Elimination Method

The goal is to eliminate one variable (e.g., $y$) to obtain a second-order ODE in terms of $x$.

**Special Case:** If $a_{12} = 0$, the equations are decoupled and can be solved independently.

**General Case (**$a_{12} \neq 0$**):**

1. From the first equation, express $y$ in terms of $\dot{x}$ and $x$:
    
    $$y = \frac{1}{a_{12}} \left( \dot{x} - a_{11}x - b_1(t) \right)$$
2. Differentiate $\dot{x}$:
    
    $$\ddot{x} = a_{11}\dot{x} + a_{12}\dot{y} + \dot{b}_1(t)$$
3. Substitute $\dot{y}$ from the second original equation:
    
    $$\ddot{x} = a_{11}\dot{x} + a_{12}(a_{21}x + a_{22}y + b_2(t)) + \dot{b}_1(t)$$
4. Substitute the expression for $y$ from step 1 into the equation above. After simplification, we obtain the characteristic second-order ODE:
    
    $$\ddot{x} - (a_{11} + a_{22})\dot{x} + (a_{11}a_{22} - a_{12}a_{21})x = a_{12}b_2(t) - a_{22}b_1(t) + \dot{b}_1(t)$$

Similarly, for $y$:

$$\ddot{y} - (a_{11} + a_{22})\dot{y} + (a_{11}a_{22} - a_{12}a_{21})y = a_{21}b_1(t) - a_{11}b_2(t) + \dot{b}_2(t)$$

### 2.2 General Solution Structure

The general solution for $x(t)$ takes the form:

$$x(t) = A u(t) + B v(t) + z(t)$$

Where $A u(t) + B v(t)$ is the complementary function (homogeneous part) and $z(t)$ is the particular integral.

**Cases for Characteristic Roots (**$r_1, r_2$**):**

- **Distinct Real Roots:** $u = e^{r_1 t}$, $v = e^{r_2 t}$.
    
- **Repeated Real Roots:** $u = e^{rt}$, $v = te^{rt}$.
    
- **Complex Roots (**$\alpha \pm \beta i$**):** $u = e^{\alpha t} \cos(\beta t)$, $v = e^{\alpha t} \sin(\beta t)$.
    

## 3. Solution Based on Eigenvalues

We can represent the homogeneous system in matrix form:

$$\dot{\mathbf{x}} = \mathbf{A}\mathbf{x} \implies \begin{pmatrix} \dot{x} \\ \dot{y} \end{pmatrix} = \begin{pmatrix} a_{11} & a_{12} \\ a_{21} & a_{22} \end{pmatrix} \begin{pmatrix} x \\ y \end{pmatrix}$$

### 3.1 Finding Eigenvalues and Eigenvectors

Trial solution: $\mathbf{x} = \mathbf{v}e^{\lambda t}$. Substituting this into the system yields the eigenvalue problem:

$$\lambda \mathbf{v} = \mathbf{A}\mathbf{v} \implies (\mathbf{A} - \lambda \mathbf{I})\mathbf{v} = \mathbf{0}$$

The eigenvalues $\lambda_{1,2}$ are found by solving the characteristic equation:

$$\det(\mathbf{A} - \lambda \mathbf{I}) = 0 \implies \lambda^2 - \text{tr}(\mathbf{A})\lambda + \det(\mathbf{A}) = 0$$$$\lambda_{1,2} = \frac{\text{tr}(\mathbf{A}) \pm \sqrt{\text{tr}(\mathbf{A})^2 - 4\det(\mathbf{A})}}{2}$$

### 3.2 General Solution

$$\begin{pmatrix} x(t) \\ y(t) \end{pmatrix} = c_1 e^{\lambda_1 t} \begin{pmatrix} v_{11} \\ v_{21} \end{pmatrix} + c_2 e^{\lambda_2 t} \begin{pmatrix} v_{12} \\ v_{22} \end{pmatrix}$$

### 3.3 Non-Homogeneous Systems

For systems with constant terms $\mathbf{b} = \begin{pmatrix} b_1 \\ b_2 \end{pmatrix}$:

1. Find the equilibrium (particular solution) $(x^*, y^*)$ by setting $\dot{x} = 0$ and $\dot{y} = 0$.
    
2. Define deviations $u = x - x^*$ and $w = y - y^*$.
    
3. The deviations follow the homogeneous system $\dot{\mathbf{u}} = \mathbf{A}\mathbf{u}$.
    

## 4. Equilibrium and Stability Analysis

### 4.1 Stability of Equilibrium

An equilibrium $(x^*, y^*)$ is **globally asymptotically stable** if:

1. $\text{tr}(\mathbf{A}) < 0$  
    
2. $\det(\mathbf{A}) > 0$
    
    This ensures that all eigenvalues have negative real parts.
    

### 4.2 Classification of Equilibrium Points

The behavior of the system near the equilibrium depends on the eigenvalues:

- **Sink:** Both eigenvalues have negative real parts (Stable).
    
- **Source:** Both eigenvalues have positive real parts (Unstable).
    
- **Center:** Purely imaginary eigenvalues (Periodic oscillations).
    
- **Saddle Point:** One positive and one negative real eigenvalue (Unstable).
    

### 4.3 Nonlinear Autonomous Systems

For a system:

$$\begin{aligned} \dot{x} &= f(x, y) \\ \dot{y} &= g(x, y) \end{aligned}$$

The stability is determined by the Jacobian matrix evaluated at the equilibrium point $(x^*, y^*)$:

$$\mathbf{J}(x^*, y^*) = \begin{pmatrix} \frac{\partial f}{\partial x} & \frac{\partial f}{\partial y} \\ \frac{\partial g}{\partial x} & \frac{\partial g}{\partial y} \end{pmatrix}$$

- If $\text{tr}(\mathbf{J}) < 0$ and $\det(\mathbf{J}) > 0$, the equilibrium is **locally asymptotically stable**.
    
- If this holds for all $(x, y)$, it is **globally asymptotically stable**.