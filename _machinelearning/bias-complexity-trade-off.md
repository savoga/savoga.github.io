---
layout: maths
name: Bias-complexity Trade-off
category: Theory
---

$\mathcal{H}$ = hypothesis class = all the classifiers that are considered

The size of $\mathcal{H}$ can be seen as a measure of complexity.

We can decompose the error of an $ERM_\mathcal{H}$ (Empiric Risk Minimization algorithm):

$$L_{\mathcal{D}}(h_s) = \epsilon_{app} + \epsilon_{est}$$

- *Approximation error*: $\epsilon_{app} = min_{h \in \mathcal{H}} L_{\mathcal{D}}(h)$. This is the error done by the best predictor among those considered. It is the *bias* we have in choosing a specific class $\mathcal{H}$.

- *Estimation error*: $\epsilon_{est} = L_{\mathcal{D}}(h) - \epsilon_{app}$. This is the error difference from a used predictor and the best one. The larger $\mathcal{H}$ (complexity), the more predictors we consider and thus the larger $\epsilon_{est}$ is likely to be.

High complexity <=> $\epsilon_{app}$ (bias) low <=> $\epsilon_{est}$ high <=> overfitting

Low complexity <=> $\epsilon_{app}$ (bias) high <=> $\epsilon_{est}$ low <=> underfitting

We also call this trade-off the **bias-variance trade-off** since a high complexity leads to a high variance. For more details on the variance, see last section of the <a class="cleanLinkSource" href="https://savoga.github.io/machinelearning/trees/">tree</a> chapter.