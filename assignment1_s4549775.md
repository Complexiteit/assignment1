---
title: Assignment 1
author: Hendrik Werner s4549775
date: \today
fontsize: 12pt
geometry: margin=5em
header-includes:
	- \usepackage{tikz}
---

# 1
Given $T(n) = T(\frac{n}{2}) + T(\frac{n}{3}) + \Theta(n)$, we want to prove that $T(n) = O(n)$.

We cannot use the Master Theorem because $T(n)$ does not match the form $T(n) = aT(\frac{n}{b}) + f(n)$, so we draw a recursion tree:

\begin{tikzpicture}
	\node (00) at (0, 0) {T(n)};
	\node[anchor=west] (d0) at (5, 0) {$n$};
	\node (10) at (-2, -1) {$T(\frac{n}{2})$};
	\node (11) at (2, -1) {$T(\frac{n}{3})$};
	\node[anchor=west] (d1) at (5, -1) {$\frac{n}{2} + \frac{n}{3}$};
	\node (20) at (-3, -2) {$T(\frac{n}{4})$};
	\node (21) at (-1, -2) {$T(\frac{n}{6})$};
	\node (22) at (1, -2) {$T(\frac{n}{6})$};
	\node (23) at (3, -2) {$T(\frac{n}{9})$};
	\node[anchor=west] (d2) at (5, -2) {$\frac{n}{4} + \frac{n}{6} + \frac{n}{6} + \frac{n}{9}$};

	\draw (00) -- (10);
	\draw (00) -- (11);
	\draw (10) -- (20);
	\draw (10) -- (21);
	\draw (11) -- (22);
	\draw (11) -- (23);
\end{tikzpicture}

$\begin{aligned}
	n &= \frac{1}{1}n &= (\frac{5}{6})^0 n\\
	\frac{n}{2} + \frac{n}{3} = \frac{3n}{6} + \frac{2n}{6} = \frac{5n}{6} &= \frac{5}{6}n &= (\frac{5}{6})^1 n\\
	\frac{n}{4} + \frac{n}{6} + \frac{n}{6} + \frac{n}{9} = \frac{54n}{216} + 2\frac{36n}{216} + \frac{24n}{216} = \frac{150n}{216} &= \frac{25}{36}n &= (\frac{5}{6})^2 n\\ 
\end{aligned}$

So our induction hypothesis is that $T(n) = cn \sum_{i = 0}^\infty (\frac{5}{6})^i = \frac{1}{1 - \frac{5}{6}}cn = \frac{1}{\frac{1}{6}}cn = 6cn, n > N$. We need to prove the hypothesis by strong induction on $n$:

$\begin{aligned}
	T(1) &= 1 + 1 + 1 \leq 6 * c * 1, c = 1\\
	T(n) &= T(\frac{n}{2}) + T(\frac{n}{3}) + cn\\
	&\stackrel{IH}{\leq} 6c\frac{n}{2} + 6c\frac{n}{3} + cn\\
	&= 3cn + 2cn + cn\\
	&= 6cn\\
\end{aligned}$

We have proven that $T(n) = 6cn$, so it follows that $T(n) = O(n)$.

# 2
Given $T(n) = 5T(\frac{n}{2}) + \Theta(n^2)$, we want to prove that $T(n) = O(n^2 \sqrt{n})$ and $T(n) = \Omega(n^2 \log n)$.

The recurrence relation matches the form $T(n) = aT(\frac{n}{b}) + f(n)$, for $a = 5, b = n, f(n) = \Theta(n^1)$, so we can apply the Master Theorem. We begin testing the first case of the theorem:

$\begin{aligned}
	f(n) &= O(n^{\log_b a - \epsilon}) & \epsilon &> 0\\
	\Theta(n^2) &= O(n^{\log_2 5 - \epsilon}) & \epsilon &> 0\\
	&= O(n^2) & \epsilon &= \log_2 5 - 2\\
\end{aligned}$

The requirement for the first case is given, so we can conclude that $T(n) = \Theta(n^{\log_2 5})$. What we want to prove is $T(n) = O(n^2 \sqrt{n})$, and $T(n) = \Omega(n^2 \log n)$.

Per the definition of $\Theta$: $T(n) = \Theta(n^{\log_2 5}) \rightarrow T(n) = O(n^{\log_2 5}) \land T(n) = \Omega(n^{\log_2 5})$.

$O(n^2 \sqrt{n}) = O(n^{2.5}) > O(n^{2.322}) \approx O(n^{\log_2 5})$, so we can conclude that $T(n) = O(n^2 \sqrt{n})$.

# 3
Given $T(n) = 2T(n - 1) + \Theta(n)$, we want to prove that $T(n) = O(2^{n + \log n})$.

\begin{tikzpicture}
	\node at (0, 0) (00) {$T(n)$};
	\node[anchor=west] at (5, 0) (d0) {$n$};
	\node at (-2, -1) (10) {$T(n - 1)$};
	\node at (2, -1) (11) {$T(n - 1)$};
	\node[anchor=west] at (5, -1) (d1) {$2(n - 1)$};
	\node at (-3, -2) (20) {$T(n - 2)$};
	\node at (-1, -2) (21) {$T(n - 2)$};
	\node at (1, -2) (22) {$T(n - 2)$};
	\node at (3, -2) (23) {$T(n - 2)$};
	\node[anchor=west] at (5, -2) (d2) {$4(n - 2)$};

	\draw (00) -- (10);
	\draw (00) -- (11);
	\draw (10) -- (20);
	\draw (10) -- (21);
	\draw (11) -- (22);
	\draw (11) -- (23);
\end{tikzpicture}

# 4
Given $T(n) = T(\frac{n}{3}) + T(\frac{2n}{3}) + 5n$, we want to prove that $T(n) = O(n \log n)$.
