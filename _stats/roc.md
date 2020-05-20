---
layout: maths
name: ROC curve
category: Predictive models
---

**ROC curve**

ROC = Receiver Operating Curve

ROC curve is used essentially for binary classification.

<ins>Use of the ROC curve</ins>

One model:

We use ROC curve to evaluate the performance of one classifying model
that we can obtain when varying a threshold.

Several models:

We use ROC curve to compare several classifying models in evaluating the
area under the curve (AUC) for a range of threshold.

<ins>Intuition</ins>

After running the prediction of a specific model, we draw the confusion
matrix (actual vs predited) with a certain threshold.

![image](/assets/img/confusionmatrice.png){: height="20%" width="20%"}

We then modify the threshold and draw another confusion matrix.

The ROC graph summarizes all of the confusion matrices that each
threshold produced.

![image](/assets/img/overlap_roc.jpeg){: height="20%" width="20%"}

On the left picture we see the ability of a model to give a clear
distinction between the two classes. The curves are drawn from the
predictions and the actual results.

<ins>Implementation</ins>

1) Get probability predictions

2) Sort the probabilities (prediction)

3) Sort the validation (actual) according to previous sort

4) Loop on the sorted validation. At each iteration:

- increment TP or FP

- compute the TPR and FPR.

5) Plot (FPR, TPR)
