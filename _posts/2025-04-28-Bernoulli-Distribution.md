---
title: Bernoulli Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🐾 Bernoulli Distribution

The **Bernoulli distribution** is a discrete distribution modeling a single trial with only two possible outcomes: success (1) or failure (0).

## 📌 Definition

Let $X \sim \text{Bernoulli}(p)$, where $0 \leq p \leq 1$. Then:

$$
P(X = x) =
\begin{cases}
p & \text{if } x = 1 \\
1 - p & \text{if } x = 0 \\
0 & \text{otherwise}
\end{cases}
$$

## 📋 Key Properties

| Property             | Value                                      |
|----------------------|---------------------------------------------|
| **Parameter(s)**     | $p \in [0, 1]$                              |
| **Support**          | $x \in \{0, 1\}$                            |
| **Mean**             | $\mathbb{E}[X] = p$                         |
| **Variance**         | $\text{Var}(X) = p(1 - p)$                  |
| **Mode**             | $1$ if $p > 0.5$, else $0$                  |
| **Entropy**          | $-p \log p - (1 - p) \log(1 - p)$           |
| **MGF**              | $M_X(t) = 1 - p + pe^t$                     |

## 🌍 Real-World Examples

1. **Email Spam Filter**  
   Whether an email is spam ($1$) or not spam ($0$) can be modeled using a Bernoulli distribution.

2. **Product Defect Detection**  
   A quality control test for a manufactured item can be modeled as success (passes inspection = $1$) or failure (defective = $0$).

## Notes
1. A Bernoulli trial is the foundation for many more complex distributions (e.g., Binomial, Geometric).
2. Models binary outcomes: yes/no, success/failure, on/off, etc.
3. Very useful in binary classification, A/B testing, digital communication, and Bayesian inference.
4. The Bernoulli is a special case of the Binomial distribution with $n = 1$.
5. If you repeat Bernoulli trials and count the number of successes, you get a Binomial distribution.

## 🐍 Python Example

```python
import numpy as np
from scipy.stats import bernoulli

# Define the probability of success
p = 0.7

# Create a Bernoulli distribution
rv = bernoulli(p)

# Sample 10 values
samples = rv.rvs(size=10)
print("Samples:", samples)

# Probability of success and failure
print("P(X=1):", rv.pmf(1))
print("P(X=0):", rv.pmf(0))

# Mean and variance
print("Mean:", rv.mean())
print("Variance:", rv.var())
```