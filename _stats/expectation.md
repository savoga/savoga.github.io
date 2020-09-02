---
layout: maths
name: Expectation
category: Tools
---

<ins>Generic definition</ins>

$X$ random variable defined on $(\Omega, \mathcal{F} ,\mathbb{P})$:

$$\mathbb{E}[X] = \int_{\Omega} X(\omega) d\mathbb{P}(\omega)$$

Using measure theory results, we find the specific cases for discrete
and continuous variables.

<ins>Discrete variables:</ins>

$$\mathbb{E}[X] = \Sigma_i x_i \mathbb{P}(X=x_i)~(= \mathbb{E}_{\mathbb{P}}[X])$$

<ins>Continuous variables:</ins>

$$\mathbb{E}[X] = \int_\mathbb{R} x f(x) dx~(= \mathbb{E}_{\mathbb{P}}[X])$$

<ins>Conditional expectation (discrete case):</ins>

$$\mathbb{E}[Y|X=x] = \Sigma_y y \mathbb{P}(Y=y | X=x)$$

It can also be written as a linear regression:

$$\mathbb{E}[Y|X=x] = \beta_0 + \beta_1 X$$