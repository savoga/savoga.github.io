---
name: Mahalanobis distance
category: Exploratory statistics
---

Mahalanobis distance

Mahalanobis distance is a good alternative to Euclidean distance. For
any given point $x$ in a set $X$, the squared Mahalanobis distance is:

$$D^2=(x-\mu_X)^T\Sigma^{-1}(x-\mu_X)$$

Advantage : it takes into account the data standard deviation and
correlation. The more the data is dispersed, the lower the distance is.
Indeed, using the inverse matrix is like if we divided the distance from
the mean $(x-\mu_X)$ by the standard deviation.

*Note*: Euclidean distance is when $\Sigma=Id$.
