---
layout: maths
name: Linear regression
category: Predictive models
---

$$Y = X \theta + \epsilon$$

Hypothesis:
$$\begin{cases}
      \mathbb{E}[\epsilon] = 0 \\
      \mathbb{V}[\epsilon] = \sigma
    \end{cases}$$

<ins>Bias</ins>

$$Bias = \mathbb{E}[\widehat{\theta}-\theta^*]$$

$$ \begin{align*}
\mathbb{E}[\widehat{\theta}] &= \mathbb{E}[(X^TX)^{-1}X^TY] \\
&= \mathbb{E}[(X^TX)^{-1}X^T(X \theta^* + \epsilon)] \\
&= \theta^* + (X^TX)^{-1}X^T\mathbb{E}[\epsilon] \\
&= \theta^*
\end{align*} $$

The estimator is **not biased**.

<ins>Variance-covariance</ins>

$$\begin{align*}
Cov(\widehat{\theta}) &= \mathbb{V}[(X^TX)^{-1}X^TY] \\
&= \mathbb{V}[(X^TX)^{-1}X^T(X \theta^* + \epsilon)] \\
&= 0 + ((X^TX)^{-1}X^T)^T\mathbb{V}[\epsilon] (X^TX)^{-1}X^T \\
&= (X^TX)^{-1}\sigma^2 ~~~~\text{ since $X^TX$ is symmetric}
\end{align*}$$

*Note*: the variance-covariance is a matrix. We define here the variance as a number.

$\mathbb{V}[\widehat{\theta}] = \mathbb{E}[(\widehat{\theta} - \mathbb{E}[\widehat{\theta}])^2]$

We know that $\|\|u\|\|_2 = \Sigma_k u_k^2 = Tr(u u^T)$.

Thus:

$$\begin{align*}
\mathbb{V}[\widehat{\theta}] &= \mathbb{E}[Tr((\widehat{\theta} - \mathbb{E}[\widehat{\theta}])(\widehat{\theta} - \mathbb{E}[\widehat{\theta}])^T)] \\
	&= Tr(\mathbb{E}[(\widehat{\theta} - \mathbb{E}[\widehat{\theta}])(\widehat{\theta} - \mathbb{E}[\widehat{\theta}])^T)] ~~~ \text{ since the trace is a number} \\
	&= Tr(Cov(\widehat{\theta})) \\
	&= Tr((X^TX)^{-1}\sigma^2) \\
	&= \sigma^2Tr((UDU^T)^{-1}) ~~~ \text{ thanks to the spectral theorem (we assume inversible matrices)} \\
	&= \sigma^2Tr((UU^T)^{-1}D^{-1}) ~~~ \text{ thanks to the trace properties} \\
	&= \sigma^2Tr(D^{-1}) ~~~ \text{ since $U$ is orthogonal} \\
	&= \sigma^2Tr(\begin{bmatrix}\frac{1}{\lambda_1} & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & \frac{1}{\lambda_p}\end{bmatrix})~~~ \text{with $\lambda_i$ the eigenvalues}  \\
	&= \sigma^2\Sigma_{k=1}^p \frac{1}{\lambda_k}
\end{align*}$$

We can see that the variance becomes **unstable** when eigenvalues are small, which is the case when variables are collinear.
