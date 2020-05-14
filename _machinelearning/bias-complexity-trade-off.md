---
layout: maths
name: Biais-complexity Trade-off
category: Theory
---

Bias-Complexity trade-off {#sec:bias-complexity-trade-off .unnumbered}
=========================

$ERM$ = Empiric Risk Minimization algorithm

$\mathcal{H}$ = hypothesis class = all the classifiers that are
considered

We can decompose the error of an $ERM_\mathcal{H}$:

$$L_{\mathcal{D}}(h_s) = \epsilon_{app} + \epsilon_{est}$$

\- *Approximation error*:
$\epsilon_{app} = min_{h \in \mathcal{H}} L_{\mathcal{D}}(h)$. This is
the error done by the best predictor among those considered.

\- *Estimation error*:
$\epsilon_{est} = L_{\mathcal{D}}(h) - \epsilon_{app}$. This is the
error difference from a used predictor and the best one.

$\epsilon_{app}$ low =\> $\epsilon_{est}$ high =\> overfitting

$\epsilon_{est}$ low =\> underfitting
