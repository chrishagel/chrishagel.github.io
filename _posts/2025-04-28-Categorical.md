---
title: Categorical Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🎨 Categorical Distribution

The **Categorical distribution** models a single draw from $k$ categories, each with its own probability.

## 📌 Definition

Let $X \sim \text{Categorical}(\mathbf{p})$, where $\mathbf{p} = (p_1, \dots, p_k)$ with $\sum p_i = 1$. Then:

$$
P(X = i) = p_i, \quad i = 1, 2, \dots, k
$$

## 📋 Key Properties

| Property             | Value                               |
|----------------------|--------------------------------------|
| **Parameters**       | $\mathbf{p} \in \Delta_k$            |
| **Support**          | $i \in \{1, \dots, k\}$              |
| **Mean**             | Not defined in scalar form           |
| **Variance**         | Not defined in scalar form           |
| **Entropy**          | $-\sum p_i \log p_i$                 |

## 🌍 Real-World Examples

1. **Rolling a Die Once**  
   One roll of a fair 6-sided die.

2. **Class Selection**  
   Randomly selecting one class label in a multi-class classifier.

## Notes

1. Generalization of the Bernoulli distribution ($k = 2$).
2. Single trial version of the Multinomial distribution.
3. Common in **machine learning**, **Bayesian modeling**, and **simulations**.

## 🐍 Python Example

```python
import numpy as np

# Probability vector
p = [0.1, 0.4, 0.5]

# Sample one categorical outcome
sample = np.random.choice(len(p), p=p)
print("Sampled index (0-based):", sample)

# Sample 10 outcomes
samples = np.random.choice(len(p), size=10, p=p)
print("Samples:", samples)
```