---
layout: maths
name: Bayes classifier
category: Theory
---

$\textbf{Bayes classifier}$

<br>

$g$ is the *classifier*.

$$g: \mathcal{X} \to \mathcal{Y}$$
$$~~~~~~~~~~\mathbb{R}^d \to \{0,1\}$$

To model the learning problem, we use the pair $(X,Y)$ described by $(\mu, \eta)$ where $\mu$ is the probability measure:

$$\mu(A) = \mathbb{P}(X \in A)$$

And $\eta$ is the regression of $Y$ on $X$:

$$\eta(X) = \mathbb{P}(Y=1 | X=x) = \mathbb{E}[Y | X=x]$$

$\eta$ is also called the *a posteriori probability*.

The Bayes classifier is:

$$\begin{cases}
      1 & \text{if}\ \eta(x) > 1/2 \\
      0 & \text{otherwise}
    \end{cases}$$

Or, if $\mathcal{Y}$ is $$\{-1,1\}$$, we write the classifier as such: $$g(x) = 2 \unicode{x1D7D9} \{ \eta(x)>1/2 \}-1$$.

<ins>Theorem</ins>:

For any classifier g: $$\mathbb{R}^d \to \{0,1\}$$,
$$\mathbb{P}(g^*(X) \neq Y) \le \mathbb{P}(g(X) \neq Y)$$

In other words, the Bayes classifier is theorically **the best classifier**.

*Proof*: express $\mathbb{P}(g(X) \neq Y) - \mathbb{P}(g^*(X) \neq Y)$ in terms of dummies (use complementaries) and show that it is superior to 0.