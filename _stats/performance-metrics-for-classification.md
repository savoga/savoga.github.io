---
layout: maths
name: Performance metrics for classification
category: Predictive models
---

1) ROC = Receiver Operating Curve

<ins>Use of the ROC</ins>

One model:

We use the ROC to evaluate the performance of one classifying model that we can obtain when varying a threshold.

Several models:

We use the ROC to compare several classifying models in evaluating the area under the curve (AUC) for a range of threshold.

<ins>Intuition</ins>

After running the prediction of a specific model, we draw the confusion matrix (actual vs predited) with a certain threshold.

![image](/assets/img/confusionmatrice.png){: height="20%" width="20%"}

We then modify the threshold and draw another confusion matrix.

The ROC summarizes all of the confusion matrices that each threshold produced.

<figure>
    <img src="/assets/img/ROC.png">
</figure>

The curve is drawn using relationship ratios between predictions and actual results:

X-axis: $$FPR = \frac{FP}{N} = \frac{FP}{FP + TN}$$

Y-axis: $$TPR = \frac{TP}{P} = \frac{TP}{TP + FN}$$

<ins>Implementation</ins>

1. Get probability predictions

2. Sort the probabilities (prediction)

3. Sort the validation (actual) according to previous sort

4. Loop on the sorted validation. At each iteration:

- increment TP or FP

- compute the TPR and FPR.

5. Plot (FPR, TPR)

See <a class="cleanLinkSource" href="https://docs.eyesopen.com/toolkits/cookbook/python/plotting/roc.html">this link</a> for an implementation example

2) PR curve = Precision-Recall curve

<figure>
    <img src="/assets/img/PR_curve.png">
</figure>

The PR curve uses the following ratios:

X-axis:

$$\text{Recall} = TPR = \frac{TP}{P} = \frac{TP}{TP + FN}$$

Y-axis:

$$\text{Precision} = \frac{TP}{TP + FP}$$

The PR curve is better adapted than the ROC in the case of imbalanced data:

ROC uses $FPR = \frac{FP}{\color{red}{N}} $ --> $N$ can be either very large or very small if classes are imbalanced.

PR curve uses $\text{Precision} = \frac{TP}{\color{green}{TP + FP}}$ --> the precision considers only the positive values coming from the model.