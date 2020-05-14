---
layout: maths
name: Online control
category: Reinforcement learning
---

**Online control**

Recall that value function is
$\forall s, V_\pi(s) = \mathbb{E}[G | s_0 = s]$

Unknown model \<=\> \"unknown strategy\" \<=\> we don't know the rewards
in advance (we need to learn *online*).

=\> we cannot compute the expectation $\mathbb{E}$

=\> instead of the value function, we will estimate the **value-action
function** thanks to the Bellman equation:

$\forall s, a,~~~~~Q_\pi(s,a) = \mathbb{E}_\pi[r_0 + \gamma Q(s_1, a_1) | s_0 = s, a_0 = a]$

=\> for an initial state and a fixed action, we can compute the $Q$
function

=\> the value-action function can be seen as the expected (=\> use of
transition matrix (probabilities)) gain we get at a state when doing a
specific action

*Note*: the policy $\pi$ takes account only from next state $s_1$

We want to *control* the policy and find the optimal one:
$\pi^*(a) = a^* \in argmax_a Q_*(s,a)$

The optimal Bellman equation becomes:

$\forall s, a,~~~~~Q_\pi(s,a) = \mathbb{E}_\pi[r_0 + \gamma max_{a'} Q(s_1, a') | s_0 = s, a_0 = a]$

How to choose initial state $a_0$?

--\> Pure exploitation: we find the best action knowing the current
system $\pi(s) \leftarrow argmax_a Q(s,a)$

=\> problem: $Q$ is estimated, thus we have a chance to miss good
actions

--\> Pure exploration: $\pi(s) \leftarrow random$

=\> problem: we can waste time on bad actions and thus have bad
estimation quality

Solution: trade-off exploitation/exploitation (SARSA, Q-learning, \...).
