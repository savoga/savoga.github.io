---
layout: maths
name: Distance metrics
category: Exploratory statistics
---

**Distance metrics**

In statistic, the generic distance metric is expressed as follow:

$$d(x,y)=(x-y)^TM(x-y)$$

where $M$ is a symmetric positive definite matrix.

*Note*: the distance is a number (1 dimension).

<ins>Euclidean distance</ins>

This is equivalent to the generic definition with $M=Id$.

Euclidean distance is also called the 2-norm: $\Sigma_{i=1}^n (x_i - y_i)^2$

<ins>Mahalanobis distance</ins>

This is equivalent to the generic definition with $M=\Sigma^{-1}$.

It is also common to define the squared Mahalanobis distance between a vector $x$ and its mean vector $\mu_x$:

$$D^2=(x-\mu_x)^T\Sigma^{-1}(x-\mu_x)$$

Advantage : it takes into account the data standard deviation and correlation. The more the data is dispersed, the lower the distance is. Indeed, using the inverse matrix is like if we divided the distance from the mean $(x-\mu_X)$ by the standard deviation.