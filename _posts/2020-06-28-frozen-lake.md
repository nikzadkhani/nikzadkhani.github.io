---
layout: distill
title: Understanding Q-Learning with OpenAI Frozen Lake
date: 2020-06-28 11:12:00-0400
description: A tutorial on q learning using OpenAI gym's frozen lake environment
comments: true
authors:
  - name: Nikzad Khani
    affiliations:
      name: Boston University
---
## Intuition
The main goal of q-learning and really a lot of other reinforcement learning algorithms is to learn an optimal policy which is
usually symbolized as $\pi$. This boils down to finding the action in every scenario that will give us the best outcome. The
policy that does this the best is called the optimal policy which is usually symbolized as $\pi^*$. Q-learning is in algorithm
to find this policy using what is called a $Q$ function.

## $Q$ Function
The $Q$ function is some function that we need to learn throught training that takes in a *state*, $s$, and an *action*, $a$, and will return the expected value of the reward. Note that the expected value will take into account the rewards of all future state-action pairs that branch after the given action.

There are a lot of different ways to learn and capture the $Q$-function. One of the most basic ways is to use a table, where
the row numbers represent different states in our environment and the columns numbers represent the actions we can take, then the
entry of the table will be the expected reward. If our Q-table perfectly captured the expected rewards for the environment, then
the optimal policy would simply entail querying the row number for the state and choosing the action whose column has the
greatest expected reward. In reality, more often than not, our expected rewards will have some error attributed to them, so our
performance will not be perfect.

## Updating the $Q$ Function
For every step in our episode we can update our $Q$-function according to the following formula

\begin{equation}
Q(s,a) = (1 - \alpha) * Q(s,a) + \alpha * (r + \gamma * Q(s', a'))
\end{equation}