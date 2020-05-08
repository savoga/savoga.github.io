---
name: Expectation-maximization (GMM)
category: Unsupervised learning
---

**Expectation-Maximization (EM) in the case of GMM (Gaussian Mixture
Model)**

(for more details, see document *gmm.pdf* in Cloud folder)

GMM problem aims at estimating parameters of a sample distribution.
(\"Generative models\" p. 295 [Understanding Machine
Learning]{.underline}).

A GMM sample is composed of $j$ Gaussian variables (*clusters*)
distributed with proportions $(\pi_1,...,\pi_k)$ ($\Sigma \pi_i =1$)

We can write:

$$X \sim \mathcal{N}(\mu_{Z},\Sigma_{Z})~~~~~~with~~Z \sim \pi$$

$\pi$ is not really a law but more the proportions of each Gaussian
categories.

Thus, $X$ has a density which is a weighted-average of all Gaussian
densities:

$$p_\theta(x) = \Sigma_{j=1}^{k}\pi_j f_j(x)~~~~~~~(*)$$

[Estimation]{.underline}

We want to estimate $\theta = (\pi, \mu, \Sigma)$ where:

$\pi=(\pi_1,...,\pi_k)$, $\mu=(\mu_1,...,\mu_k)$,
$\Sigma=(\Sigma_1,...,\Sigma_k)$

To do so, we use the maximum likelihood method (product of densities
across all samples):

$$p_\theta(x)=\Pi_{i=1}^n p_\theta(x_i)$$

$$l(\theta)=log(\Pi_{i=1}^n p_\theta(x_i))=\Sigma_{i=1}^n log(p_\theta(x_i))$$

We thus need to find $argmax(l(\theta))$

Problem: the likelihood function is not convex!

The expectation-maximization problem is used when we have *latent
variables* (= variables for which we don't know their associated
distribution).

Let $z=(z_1,...,z_k)$ be the vector of latent variables. We can express
the density $(*)$ as a joint function with respect to $z$:

$$p_\theta(x,z)=p_\theta(z)p_\theta(x|z)$$

$$l(\theta, z) = ... =\Sigma(log \pi_{z_i})+ \Sigma(logf_{z_i}(x_i))$$

A classic optimization (in case of Gaussians) give us empirical values
as solutions e.g. $\hat{\pi_j}=\frac{n_j}{n}$

Problem: we don't know $j$!

We will thus use the *expected* log-likelihood method.

Let us find another expression of the likelihood:

$$p_\theta(x,z)=p_\theta(x)p_\theta(z|x)$$

As seen previously: $p_\theta(x,z)=\Pi \pi_{z_i}f_{z_i}(x_i)$

$p_\theta(z|x)=\Pi p_\theta(z_i|x_i)=\frac{\Pi \pi_{z_i}f{z_i}(x_i)}{p_\theta(x_i)} \propto \Pi \pi_{z_i}f{z_i}(x_i)$

Given an initial parameter $\theta_0$, the *expected* log-likelihood is
written as such:

$$\mathbb{E}_{\theta_0}[l(\theta;z)]=\Sigma p_{\theta_0}(z|x) l(\theta;z)$$
$$\mathbb{E}_{\theta_0}[l(\theta;z)]=\Sigma_{j} \Sigma_{i} p_{ij}(log\pi_j+logf_j(x_i))$$

We now have an expression that doesn't depend on $z$ but only on
$p_{ij}$ and we know that $n_j=\Sigma_i p_{ij}$
