---
layout: maths
name: AdaBoost
category: Supervised learning
---

**AdaBoost**

Boosting is an algorithmic paradigm addressing two major issues in
machine learning:

- It optimizes the <a class="cleanLinkSource" href="https://savoga.github.io/machinelearning/bias-complexity-trade-off">biais-complexity trade-off</a>. The learning starts with a basic class (large
approximation error) and as it progresses the hypothesis class becomes
more complex.

- It allows to find predictors that are usually computationally
infeasible to find.

Main idea: weak learners are \"boosted\" to become stronger altogether.

<figure>
    <img src="/assets/img/AdaBoost_Schema.png">
</figure>

Weak learner (or $\gamma$-weak-learner): it's an **algorithm** returning
a function $h$ such that $L_{\mathcal{D}}(h) \leq 1/2 - \gamma$. In
other words, it returns a simple binary predictor that does slightly
better than a random guess.

<figure>
    <img src="/assets/img/adaboost-algo.png">
</figure>

We note:

- Final predictor = weighted sum of weak predictors

- More weights are given to observations that gave wrong prediction. In
doing so, the classifier of the next round will focus on these
observations. Warning: to see this, focus on the variation of
$D^{(t+1)}_i$ and not just $w_t$.

Theorem: the training error of the output hypothesis decreases
**exponentially fast** with the number of boosting rounds.
