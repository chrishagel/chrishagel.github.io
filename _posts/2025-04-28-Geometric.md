---
title: Geometric Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🎲 Geometric Distribution

The **Geometric distribution** models the number of trials until the first success in a sequence of independent Bernoulli trials.

## 📌 Definition

Let $X \sim \text{Geometric}(p)$. Then:

$$
P(X = k) = (1 - p)^{k - 1} p, \quad k = 1, 2, 3, \dots
$$

## 📋 Key Properties

| Property             | Value                              |
|----------------------|--------------------------------------|
| **Parameter**        | $p \in (0, 1]$                      |
| **Support**          | $k \in \{1, 2, 3, \dots\}$          |
| **Mean**             | $\mathbb{E}[X] = \frac{1}{p}$       |
| **Variance**         | $\text{Var}(X) = \frac{1 - p}{p^2}$ |
| **Mode**             | $1$                                 |
| **MGF**              | $M_X(t) = \frac{pe^t}{1 - (1 - p)e^t}$, for $t < -\log(1 - p)$ |

## 🌍 Real-World Examples

1. **Sales Calls**  
   Number of calls until the first sale is made, where each has a success rate of 10%.

2. **Dice Rolls**  
   Number of rolls until the first six appears.

## Notes

1. Memoryless: $P(X > m + n \mid X > m) = P(X > n)$.
2. Models "wait time" for first success.
3. Special case of the negative binomial with $r = 1$.
4. Can be shifted to start from $0$ (alternative definition).

## 🐍 Python Example

```python
from scipy.stats import geom

p = 0.3
rv = geom(p)

# PMF at a specific value
print("P(X=4):", rv.pmf(4))

# Sample 10 values
print("Samples:", rv.rvs(size=10))

# Mean and variance
print("Mean:", rv.mean())
print("Variance:", rv.var())
