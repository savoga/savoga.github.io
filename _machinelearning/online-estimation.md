---
layout: maths
name: Online estimation
category: Reinforcement learning
---

**Online estimation**

The expected value function is approached using empiric estimator (sum).

Two ways to do it:

- Monte-Carlo update: if we can memorize all the paths, we update the
sum at each step $S \leftarrow x_t$. At the end we compute the mean
$X \leftarrow \frac{S}{t}$

- TD-learning: we update the value function using temporal differences
$\forall s, V(s_t) \xleftarrow{\alpha} r_t + \gamma V(s_{t+1})$ where $X \xleftarrow{\alpha} x_t <=> X = X + \alpha (x_t - X)$ ($\alpha$
is usually $1/t$)
