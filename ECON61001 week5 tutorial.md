---
ContentType: " handwritten"
date: 2026-01-05
tags:
  - topic/econ/emet
modified: false
aliases:
  - log-normal distribution
---
# ECON61001: Tutorial Notes

## Topic: Log-normal Distribution and Expectation Derivation

This document outlines the mathematical derivation for the expectation of a log-normally distributed random variable and its application in regression analysis.

### 1. Definition and Setup

Let $w$ be a random variable such that its natural logarithm follows a normal distribution:

$$y = \ln(w) \implies y \sim N(\mu, \sigma^2)$$

This implies that:

$$w = e^y$$

Our objective is to calculate the expected value $E[w]$.

### 2. Mathematical Derivation of $E[w]$  

The expected value is defined by the integral:

$$E[w] = \int_{-\infty}^{+\infty} e^y \cdot f(y) \, dy$$

Substituting the probability density function (PDF) of the normal distribution for $y$:

$$E[w] = \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( -\left[ \frac{(y-\mu)^2}{2\sigma^2} - y \right] \right) \, dy$$

#### 2.1 Completing the Square Using Variable $m$  

To simplify the exponent, we aim to relate the current expression to the kernel of a new normal distribution $N(\mu + \sigma^2, \sigma^2)$. Following the handwritten notes, we set up the following identity by adding a constant term $m$:

$$\frac{(y - \mu)^2}{2\sigma^2} - y = \frac{(y - (\mu + \sigma^2))^2}{2\sigma^2} + m$$

Rearranging the equation to solve for $m$:

$$m = \frac{(y - \mu)^2 - (y - (\mu + \sigma^2))^2}{2\sigma^2} - y$$

Using the difference of squares formula $a^2 - b^2 = (a-b)(a+b)$ to simplify the numerator:

$$m = \frac{\left[ (y - \mu) - (y - \mu - \sigma^2) \right] \left[ (y - \mu) + (y - \mu - \sigma^2) \right]}{2\sigma^2} - y$$$$m = \frac{(\sigma^2)(2y - 2\mu - \sigma^2)}{2\sigma^2} - y$$$$m = \frac{2y - 2\mu - \sigma^2}{2} - y = (y - \mu - \frac{\sigma^2}{2}) - y$$$$m = -\mu - \frac{\sigma^2}{2}$$

Thus, the original exponent in the integral can be rewritten as:

$$-\left[ \frac{(y - \mu)^2}{2\sigma^2} - y \right] = -\frac{(y - (\mu + \sigma^2))^2}{2\sigma^2} - m = -\frac{(y - (\mu + \sigma^2))^2}{2\sigma^2} + \left( \mu + \frac{\sigma^2}{2} \right)$$

#### 2.2 Final Integration

Substituting this back into the expectation integral:

$$E[w] = \int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( -\frac{(y - (\mu + \sigma^2))^2}{2\sigma^2} + \left( \mu + \frac{\sigma^2}{2} \right) \right) \, dy$$$$E[w] = e^{\mu + \frac{\sigma^2}{2}} \cdot \underbrace{\int_{-\infty}^{+\infty} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( -\frac{(y - (\mu + \sigma^2))^2}{2\sigma^2} \right) \, dy}_{=1}$$

Since the integral of a normal PDF over its entire domain is 1, we arrive at the final result:

$$E[w] = e^{\mu + \frac{\sigma^2}{2}}$$

### 3. Application in Regression Analysis

In the context of an exponential regression model:

$$\ln(y) = x' \beta_0 + u$$

Where $u \sim N(0, \sigma_0^2)$. To find the expected value of the original dependent variable $y$:

$$y = \exp(x' \beta_0 + u)$$$$E[y|x] = \exp(x' \beta_0) \cdot E[\exp(u)]$$

Using the result derived above (where $\mu = 0$ and $\sigma^2 = \sigma_0^2$ for the error term $u$):

$$E[\exp(u)] = \exp\left(0 + \frac{\sigma_0^2}{2}\right) = \exp(0.5 \sigma_0^2)$$

Therefore:

$$E[y|x] = \exp(x' \beta_0 + 0.5 \sigma_0^2)$$