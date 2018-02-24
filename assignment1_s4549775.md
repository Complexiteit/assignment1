---
title: Assignment 1
author: Hendrik Werner s4549775
date: \today
fontsize: 12pt
geometry: margin=5em
---

# 1
Given $T(n) = T(\frac{n}{2}) + T(\frac{n}{3}) + \Theta(n)$, we want to prove that $T(n) = O(n)$.

We cannot use the Master Theorem because $T(n)$ does not match the form $T(n) = aT(\frac{n}{b}) + f(n)$.

# 2
Given $T(n) = 5T(\frac{n}{2}) + \Theta(n^2)$, we want to prove that $T(n) = O(n^2 \sqrt{n})$ and $T(n) = \Omega(n^2 \log n)$.

The recurrence relation matches the form $T(n) = aT(\frac{n}{b}) + f(n)$, for $a = 5, b = n, f(n) = \Theta(n^1)$, so we can apply the Master Theorem. We begin testing the first case of the theorem:

$\begin{aligned}
	f(n) &= O(n^{\log_b a - \epsilon}) & \epsilon &> 0\\
	\Theta(n^2) &= O(n^{\log_2 5 - \epsilon}) & \epsilon &> 0\\
	&= O(n^2) & \epsilon &= \log_2 5 - 2\\
\end{aligned}$

The requirement for the first case is given, so we can conclude that $T(n) = \Theta(n^{\log_2 5})$

# 3
Given $T(n) = 2T(n - 1) + \Theta(n)$, we want to prove that $T(n) = O(2^{n + \log n})$.

# 4
Given $T(n) = T(\frac{n}{3}) + T(\frac{2n}{3}) + 5n$, we want to prove that $T(n) = O(n \log n)$.
