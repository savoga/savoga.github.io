---
layout: maths
name: Performance metrics using likelihood
category: Predictive models
---

AIC (Akaike Information Criterion) and BIC (Bayesian Information Criterion) are based on a trade-off between model accuracy and model complexity.

Those criteria have foundations in *information theory*: it measures the **loss of information**. The lower the metrics, the less information a model losses thus the higher the quality of that model.

$$AIC = -2\ln L(\hat \theta) + 2k$$

$$BIC = -2\ln L(\hat \theta) + ln(n)k$$

$L(\hat \theta)$ = the maximized value of the likelihood function of the model, i.e. $L(\hat \theta)= \mathbb{P}(x \mid \hat \theta)$ where $\hat \theta$ are the parameter values that maximize the likelihood function and $x$ the observed data.

$k$ is the number of parameters in the model.

$n$ is the sample size.


The first term is the **risk of underfitting**: we want the highest probability to observe a behavior under specific parameters. It measures how well adapted is our model for our data. The more parameters we have, the better the model is. We also call it the *goodness of fit*.

The second term **risk of overfitting**: we want to penalize models with high number of parameters because the more we increase this number the more the model becomes complex.

The main difference between the two metrics is that BIC penalizes more overfitting because of the $n$ term. Consequently, for large sample sizes, BIC will favor models with few parameters compared with AIC.