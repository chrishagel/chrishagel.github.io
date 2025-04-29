---
title: Hyper Geometric Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🧪 Hypergeometric Distribution

The **Hypergeometric distribution** models the number of successes in a sample drawn *without replacement* from a finite population.

## 📌 Definition

Let $X \sim \text{Hypergeometric}(N, K, n)$, where:

- $N$ = population size  
- $K$ = number of success states in the population  
- $n$ = number of draws

Then:

$$
P(X = k) = \frac{\binom{K}{k} \binom{N - K}{n - k}}{\binom{N}{n}}
$$

## 📋 Key Properties

| Property             | Value                                                        |
|----------------------|---------------------------------------------------------------|
| **Parameters**       | $N \in \mathbb{N}, K \in [0, N], n \in [0, N]$                |
| **Support**          | $k \in [\max(0, n - N + K), \min(n, K)]$                      |
| **Mean**             | $\mathbb{E}[X] = n \cdot \frac{K}{N}$                         |
| **Variance**         | $\text{Var}(X) = n \cdot \frac{K}{N} \cdot \left(1 - \frac{K}{N}\right) \cdot \frac{N - n}{N - 1}$ |
| **Mode**             | $\left\lfloor \frac{(n + 1)(K + 1)}{N + 2} \right\rfloor$     |

## 🌍 Real-World Examples

1. **Quality Testing**  
   Drawing 10 items from a shipment of 100, 20 of which are defective. How many defective in your sample?

2. **Card Games**  
   Probability of getting exactly 2 hearts in a 5-card hand from a standard deck.

## Notes

1. No replacement: dependencies between trials.
2. Cannot be modeled with binomial because trials are not independent.
3. Useful in finite sampling and acceptance testing.
4. Variance shrinks faster than in binomial due to decreasing population.

## 🐍 Python Example

```python
from scipy.stats import hypergeom

# N = total population, K = total successes, n = sample size
N, K, n = 50, 10, 5
rv = hypergeom(N, K, n)

# PMF at a specific value
print("P(X=2):", rv.pmf(2))

# Sample 10 values
print("Samples:", rv.rvs(size=10))

# Mean and variance
print("Mean:", rv.mean())
print("Variance:", rv.var())
