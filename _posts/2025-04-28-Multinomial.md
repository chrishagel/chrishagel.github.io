---
title: Multinomial Distribution
date: 2025-04-28
categories: ["Zoos", "Distribution Zoo"]
tags: [distributions, discrete]     # TAG names should always be lowercase
math: true
---

# 🧮 Multinomial Distribution

The **Multinomial distribution** generalizes the Binomial: it models the counts of outcomes in multiple categories from a fixed number of independent trials.

## 📌 Definition

Let $X = (X_1, \dots, X_k) \sim \text{Multinomial}(n, \mathbf{p})$, where:

- $n$ is the number of trials,
- $\mathbf{p} = (p_1, \dots, p_k)$ is a probability vector such that $\sum p_i = 1$.

Then:

$$
P(X_1 = x_1, \dots, X_k = x_k) = \frac{n!}{x_1! \cdots x_k!} p_1^{x_1} \cdots p_k^{x_k}
$$

subject to $\sum x_i = n$.

## 📋 Key Properties

| Property             | Value                                          |
|----------------------|------------------------------------------------|
| **Parameters**       | $n \in \mathbb{N}$, $\mathbf{p} \in \Delta_k$  |
| **Support**          | $x_i \in \{0, \dots, n\}$, $\sum x_i = n$     |
| **Mean**             | $\mathbb{E}[X_i] = np_i$                       |
| **Variance**         | $\text{Var}(X_i) = np_i(1 - p_i)$              |
| **Covariance**       | $\text{Cov}(X_i, X_j) = -np_ip_j$, $i \neq j$ |

## 🌍 Real-World Examples

1. **Dice Rolls**  
   Number of times each face appears in 60 rolls of a fair 6-sided die.

2. **Survey Responses**  
   Count of responses in a multiple-choice survey with 4 options.

## Notes

1. Reduces to Binomial when $k = 2$.
2. Often used in **NLP**, **classification**, and **contingency tables**.
3. Describes outcomes of **n categorical trials**.

## 🐍 Python Example

```python
from numpy.random import multinomial

# n = number of trials, p = probability vector
n = 10
p = [0.2, 0.3, 0.5]

# Sample a single multinomial outcome
sample = multinomial(n, p)
print("Sample:", sample)