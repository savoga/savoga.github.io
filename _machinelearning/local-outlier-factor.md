---
layout: maths
name: Local Outlier Factor
category: Unsupervised learning
---

**Local Outlier Factor**

Local Outlier Factor is an unsupervised method used in anomaly
detection. It consists of comparing local density of train observations
VS local density of test observations.

<ins>Reachability distance</ins>

$$reachability \mbox{-} distance_k(A,B) = max \{ k \mbox{-} distance (B), d(A,B)\}$$
= reachability of A *from* B.

$k \mbox{-} distance (B)$: distance from B to its kth nearest neighbor.

The reachability distance of A from B is *at least* the distance between
A and B or *at least* the distance of B's neighbor.

When A is very far from B, it's simply the distance between the two
points.

When A is very close to B, it's the distance between B and its
neighbor.

The distance can be computed using different metrics: Euclidean
distance, Mahalanobis distance, etc.

<ins>Local reachability density</ins>

$$lrd_k (A) = \frac{1}{\Sigma_{B \in N_k(A)} reachability \mbox{-} distance_k(A,B) / |N_k(A)|}$$

It's the inverse of the average of reachability-distances of A from B.

When A is very far from its neighbors: sum of reachability distances is
high => local reachability density is small.

<ins>Local Outlier Factor</ins>

LOF computation consists of comparing the local densities of a point VS
its neighbors.
$LOF_k(A) : =  \frac{\frac{\Sigma_{B \in N_k(A)}lrd_k(B)}{lrd_k(A)}}{|N_k(A)|}$

$LOF_k(A) > 1$: A is an outlier. Local reachability density of A is
small compared to its neighbors.

$LOF_k(A) < 1$: A is an inlier.

<figure>
    <img src="\assets\img\LOF.png"/>
</figure>

On this figure, $k = 3$. We can see that the reachability distance of A
from its neighbors is high (red segments). The local reachability
density of A will thus be **low**.

On the contrary, the local reachability densities of its neighors is
**high** because each neighbor can be easily reached from their own
neighbors.

As a result, LOF would be high so A is an outlier.

<ins>sklearn algorithm</ins>

To score an observation, *fit* simply memorizes the train observations
(same as in knn).

*score\_samples* first finds the k-nearest neighbors from the train set
thanks to the given distance metric. It then computes the local outlier
factor for each test observation comparing the test observation local
density with its closest k-neighbors local densities in the train set.
