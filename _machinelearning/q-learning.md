---
layout: maths
name: Q-learning
category: Reinforcement learning
---

**Q-learning**

This algorithm is also based on $\epsilon$-greedy algorithm.

$$\pi(s) \leftarrow
    \begin{cases}
     a^* \in argmax_a Q(s,a) & \text{with probability}~1-\epsilon \\
    random & \text{with probability}~\epsilon
    \end{cases}$$

<ins>Estimation</ins>: unlike SARSA, Q-learning aims at updating the estimator
using the best action at each iteration:

$\forall t, Q(s_t, a_t) \xleftarrow{\alpha} r_t + \gamma max_{a} Q(s_{t+1}, a)$

The only modification from SARSA is the following line:

```
Q[state_prev, action_prev] = (1 - alpha) *  Q[state_prev, action_prev] + alpha * (rewards[action_prev] + gamma * np.max(Q[state].data))
```