---
layout: maths
name: Fairness metrics
category: Inferential statistics
---

How can we make sure the model doesn’t discriminate any group? To answer this question, we first have to define a **sensitive attribute**. This attribute is the criteria we want to assess the fairness with respect to.

In the case of a bank, we can think about a model predicting whether a client will default. We can take **client gender** as a sensitive attribute. Then the question becomes: are we sure men and women are equally likely to be granted a loan?

*Statistical Parity*

Statistical Parity, also called Demographic Parity or Group Fairness, aims at comparing proportions of predictions conditioned on the sensitive attribute.

$$\mathbb{P}(\hat Y= 1|A=a) =\mathbb{P}(\hat Y= 1|A=b)$$

Where $A$ is the sensitive attribute (e.g. gender). From a statistical perspective, this metric consists of comparing two distributions of $\hat Y$: one conditioned on $A = a$ and one conditioned on $A=b$. More details can be found on the metric in this <a class="cleanLinkSource" href="https://arxiv.org/pdf/1701.08230.pdf">article</a>.

The next two metrics are thoroughly explained in this <a class="cleanLinkSource" href="https://arxiv.org/pdf/1610.02413.pdf">article</a> and this <a class="cleanLinkSource" href="https://arxiv.org/pdf/1701.08230.pdf">article</a>. Their main advantages over Statistical Parity is that **they account for correlation between the target value and the sensitive attribute**.

*Equal Opportunity*

$$\mathbb{P}(\hat Y= 1|A=a,Y= 1) = \mathbb{P}(\hat Y= 1|A=b,Y= 1)$$

Here we focus only on positive outcome. In other words, we measure how fair the model is when it successfully predicts that clients will default. This definition is also equivalent to comparing True Positive Rates.

*Predictive Equality*

$$\mathbb{P}(\hat Y= 1|A=a,Y= 0) = \mathbb{P}(\hat Y= 1|A=b,Y= 0)$$

Here we focus only on negative outcome. In other words, we measure how fair the model is when it wrongly predicts that clients will default. This definition is also equivalent to comparing False Positive Rates.