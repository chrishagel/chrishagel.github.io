---
title: Negative Binomial Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🎯 Negative Binomial Distribution

The **Negative Binomial distribution** models the number of trials needed to achieve a fixed number of successes in independent Bernoulli trials.

## 📌 Definition

Let $X \sim \text{NegBin}(r, p)$, where:

- $r$ is the number of **successes** we are waiting for,
- $p$ is the probability of success on each trial.

Then:

$$
P(X = k) = \binom{k - 1}{r - 1} p^r (1 - p)^{k - r}, \quad k = r, r + 1, \dots
$$

Alternatively, some definitions let $X$ count **failures before the $r$-th success**:

$$
P(X = k) = \binom{k + r - 1}{r - 1} p^r (1 - p)^k, \quad k = 0, 1, 2, \dots
$$

## 📋 Key Properties

| Property             | Value                                                        |
|----------------------|---------------------------------------------------------------|
| **Parameters**       | $r \in \mathbb{N}$, $p \in (0, 1]$                            |
| **Support**          | $k \in \{r, r + 1, \dots\}$ or $\{0, 1, \dots\}$ (alternate)  |
| **Mean**             | $\mathbb{E}[X] = \frac{r}{p}$                                 |
| **Variance**         | $\text{Var}(X) = \frac{r(1 - p)}{p^2}$                        |
| **Mode**             | $\left\lfloor \frac{(r - 1)(1 - p)}{p} \right\rfloor + r$     |
| **MGF**              | $M_X(t) = \left(\frac{p e^t}{1 - (1 - p)e^t}\right)^r$ for $t < -\log(1 - p)$ |

## 🌍 Real-World Examples

1. **Customer Signups**  
   How many trials (ads, emails, visits) are needed to get 5 customer signups, if each contact has a 10% chance of converting?

2. **Manufacturing**  
   How many defective parts will be found before identifying 3 non-defective parts on a faulty production line?

## Notes

1. Generalizes the geometric distribution: Geometric is a special case with $r = 1$.
2. Models **waiting time** for $r$ successes.
3. Often used when data shows **overdispersion** (variance > mean).
4. Can be parameterized in terms of **failures** or **trials**, depending on context.
5. Appears in **count models** in statistics, e.g., in negative binomial regression.

## 🐍 Python Example

```python
from scipy.stats import nbinom

# r = number of successes, p = probability of success
r, p = 3, 0.4

# SciPy's nbinom counts failures before the r-th success
rv = nbinom(r, p)

# PMF at a specific value (e.g., 5 failures before 3 successes)
print("P(X=5):", rv.pmf(5))

# Sample 10 values
print("Samples:", rv.rvs(size=10))

# Mean and variance
print("Mean:", rv.mean())
print("Variance:", rv.var())
```