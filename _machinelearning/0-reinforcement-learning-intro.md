---
name: Intro
category: Reinforcement learning
---

Reinforcement learning is inspired on human logic: we learn which
strategy to take thanks to rewards we receive.

Reinforcement learning uses Markov Decision Processes (MDP).

A Markov Decision Process is defined by:

\- an initial state $s_0$

\- the reward distribution $r_t \sim p(r | s_t, a_t)$ (stochastic)

\- the transition probabilities, $s_{t+1} \sim p(s | s_t, a_t)$
(stochastic)

=\> **MDP: we know the state and the reward from the previous state
only**.

A *policy* is an action for each state, for a given MDP.

=\> **a policy can be seen as a strategy: we know where to go at each
state**. In practice the policy is actually the **transition probability
matrix**.

The *value function* is the gain we earn at a state, for a specific
policy: $\forall s, V_\pi(s) = \mathbb{E}_{\pi}[G | s_0 = s]$

=\> **The expected gain takes into account the transition probability.**

The gain is calculated as such:
$G = r_0 + \gamma r_1 + \gamma^2 r_2 +... = \Sigma_t \gamma^t r_t$ where
$\gamma$ is the *discount factor*.

$V$ can also be written
$V_\pi(s) = \mathbb{E}_\pi[r_0 + \gamma V(s_1) | s_0 = s]$. This
expression is called **Bellman equation**.

We can find the best policy:

$\forall s, \pi^*(s) = a^* \in argmax_a\mathbb{E}_\pi[r_0 + \gamma V_*(s_1) | s_0 = s, a_0 = a]$

Where $V_*$ is solution of the **Bellman optimality equation**:

$\forall s, V(s) = max_a\mathbb{E}[r_0 + \gamma V(s_1) | s_0 = s]$
