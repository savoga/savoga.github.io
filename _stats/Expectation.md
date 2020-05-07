---
name: Expectation
category: Tools
---

$\textbf{Expectation}$

<br>

Generic definition:

$X$ random variable defined on $(\Omega, \mathcal{F} ,\mathbb{P})$:

$\mathbb{E}[X] = \int_{\Omega} X(\omega) d\mathbb{P}(\omega)$

<br>

Using measure theory results, we find the specific cases for discrete and continuous variables.

For discrete variables :

$\mathbb{E}[X] = \Sigma_i x_i \mathbb{P}(X=x_i)~(= \mathbb{E}_{\mathbb{P}}[X])$

For continuous variables:

$\mathbb{E}[X] = \int x f(x) dx~(= \mathbb{E}_{\mathbb{P}}[X])$

<br>

Conditional expectation (discrete case):

$\mathbb{E}[Y \| X=x] = \Sigma_y y \mathbb{P}(Y \| X=x)$