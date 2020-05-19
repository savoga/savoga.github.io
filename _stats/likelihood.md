---
layout: maths
name: Likelihood method
category: Tools
---

**Likelihood method**

This method consists on finding the parameter that maximizes the
likelihood of an event. It is usually done when we know the type of law
of a random variable (uniform, gaussian etc.) and we are looking for the
parameter that maximizes the likelihood ($\approx$ probability) that an
event occurs.

$L(\theta; x_1,...,x_n) = \prod_{i=1}^{n}f(x_i;\theta)$ which is the
product of densities across all samples.

In discrete form:
$L(\theta; x_1,...,x_n) = \prod_{i=1}^{n}\mathbb{P}(X = x_i; \theta)$

*Note (wording clarification)*:
$L(\theta | X) = \mathbb{P} (X | \theta)$

- $\mathbb{P} (X | \theta)$: the probability of observing an event with
fixed model parameters.

- $L(\theta | X)$: the likelihood of the parameters taking certain values
given that we observe an event.

Intuitively, we want to find the $\theta$ that maximizes a certain
event, that is, obtaining some data $X$ (which is why we have
$X | \theta$).

We often use the log in order to get rid of power coefficients appearing
with the product.

*likelihood equation*: $\frac{d}{d\theta}ln(L(x_1,...,x_n;\theta))=0$

*Note*: in machine learning, we use likelihood maximization in
unsupervised learning when we want to estimate parameters of a
distribution sample (generative models).
