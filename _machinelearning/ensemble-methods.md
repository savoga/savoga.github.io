---
layout: maths
name: Ensemble methods
category: Supervised learning
---

Ensemble methods are good to reduce variance.

There are several types of ensemble methods:

<ins>Bagging</ins> (Random Forests)

Bagging methods reduce variance and handle overfitting.

Predictors are chosen independently.

<ins>Boosting</ins> (AdaBoost, Gradient Boosting)

Boosting methods have the advantage of reducing the variance and the bias. However, these algorithms can overfit.

Predictors are chosen sequentially: predictors learn from the mistakes of the previous ones. The choice of the stopping criteria is critical to prevent overfitting.