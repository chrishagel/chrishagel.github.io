---
title: Binomial Distibution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🎯 Binomial Distribution

The **Binomial distribution** models the number of successes in a fixed number of independent Bernoulli trials.

## 📌 Definition

Let $X \sim \text{Binomial}(n, p)$, where $n$ is the number of trials and $p$ is the probability of success on each trial. Then:

$$
P(X = k) = \binom{n}{k} p^k (1 - p)^{n - k}, \quad k = 0, 1, \dots, n
$$

## 📋 Key Properties

| Property             | Value                                            |
|----------------------|--------------------------------------------------|
| **Parameters**       | $n \in \mathbb{N}$, $p \in [0, 1]$               |
| **Support**          | $k \in \{0, 1, \dots, n\}$                        |
| **Mean**             | $\mathbb{E}[X] = np$                             |
| **Variance**         | $\text{Var}(X) = np(1 - p)$                      |
| **Mode**             | $\lfloor (n + 1)p \rfloor$ (or $\lceil (n + 1)p \rceil - 1$) |
| **MGF**              | $M_X(t) = (1 - p + pe^t)^n$                      |

## 🌍 Real-World Examples

1. **Survey Results**  
   Out of 100 people, how many support a candidate if each has a 0.6 probability of supporting them?

2. **Quality Control**  
   Count how many out of 20 light bulbs pass inspection, where each has a 95% chance of being good.

## Notes

1. The sum of $n$ independent Bernoulli($p$) variables.
2. Used for modeling number of successes in fixed-size samples.
3. Central to hypothesis testing and confidence interval estimation.
4. Approaches normal distribution as $n$ increases (Central Limit Theorem).

## 🐍 Python Example

```python
from scipy.stats import binom

n, p = 10, 0.5
rv = binom(n, p)

# PMF at a specific value
print("P(X=3):", rv.pmf(3))

# Sample 10 values
print("Samples:", rv.rvs(size=10))

# Mean and variance
print("Mean:", rv.mean())
print("Variance:", rv.var())
