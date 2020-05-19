---
layout: maths
name: SARSA
category: Reinforcement learning
---

**SARSA**

This algorithm is based on $\epsilon$-greedy algorithm.

$$\pi(s) \leftarrow
    \begin{cases}
     a^* \in argmax_a Q(s,a) & \text{with probability} & 1-\epsilon \\
    random & \text{with probability} & \epsilon
    \end{cases}$$

=> with a small probability ($\epsilon$ is usually lower than $5\%$),
we do random actions. Otherwise we take the best action of the known
ones.

**Estimation** is done through *TD-learning* (temporal differences - see
Online Estimation):

$$\forall t, Q(s_t, a_t) \xleftarrow{\alpha} r_t + \gamma Q(s_{t+1}, a_{t+1})$$

    # action is identified with new state (after move)
    # Q is the transition probability matrix: rows = states and columns = actions

    def sarsa(Q, model = model, alpha = 0.1, eps = 0.1, n_iter = 100):
        states = model.states
        terminals = model.terminals
        rewards = model.rewards
        gamma = model.gamma
        # random state (not terminal)
        state = np.random.choice(np.setdiff1d(np.arange(len(states)), terminals))
        # random action
        action = np.random.choice(Q[state].indices)
        new_state = action
        for t in range(n_iter):
            state_prev = state
            action_prev = action
            state = new_state
            if state in terminals: # if the new action gives terminal state we start again from a new random state
                    state = np.random.choice(np.setdiff1d(np.arange(len(model.states)),terminals))
                    action = np.random.choice(Q[state].indices)
                    Q[state_prev, action_prev] = (1 - alpha) *  Q[state_prev, action_prev] + alpha * rewards[action_prev]
                    # we removed the second term since state_prev was the last step
            else:
                    # we choose the best action that has the highest expected value-action
                    best_action = Q[state].indices[np.argmax(Q[state].data)]
                    if np.random.random() < eps: 
                    # with probability of epsilon, we choose a random action
                        action = np.random.choice(Q[state].indices)
                    else:
                        action = best_action
                    Q[state_prev, action_prev] = (1 - alpha) *  Q[state_prev, action_prev] + alpha * (rewards[action_prev] + gamma * Q[state, action])
            new_state = action
        return Q