---
layout: post
---

# Regret Minimization in Games with Incomplete Information

[this paper](https://proceedings.neurips.cc/paper/2007/file/08d98638c6fcd194a4b1e6992063e944-Paper.pdf).

This paper describes a new technique for finding approximate solutions to large extensive games. They authors show that minimizing counterfactual regret minimizes overall regret.

## What is Regret?

In Poker, we deal with incomplete information and uncertainity.

Regret is the difference between the payoff of the best possible action and the payoff of the action taken; in poker, it is how much you wish you had played a different hand.

Extensive games with incomplete information, like poker, are a vital area in game theory, focusing on regret—the player's wish for different past actions based on current knowledge. These games model sequential decision-making amid imperfect information, where players' actions shape the information available to others. Extensive games provide a general yet compact model of multiagent interaction, which explicitly represents the often sequential nature of these interactions.

Just FYI, MDPs and POMDPs models (used in reinforcement learning) are solo decision-making under uncertainty, while extensive games involve strategic interactions among multiple decision-makers.

Chess and Go are perfect information games. Poker is an example of an extensive game with incomplete information.

If all players can recall their previous actions and the corresponding information sets, the game is said to be one of **perfect recall**. This work will focus on finite, zero-sum extensive games with perfect recall.

## Nash Equilibrium

In a two-player extensive game, a Nash equilibrium is a strategy profile $$( \sigma )$$ where:

$$
u_1(\sigma) \geq \max_{ \sigma'_1 \in \Sigma _1} u_1(\sigma'_1, \sigma_ 2)
$$

$$
u_2(\sigma) \geq \max_{ \sigma'_2 \in \Sigma_ 2} u_2(\sigma_ 1, \sigma'_2)
$$


An approximation of a Nash equilibrium or $$( \epsilon )$$-Nash equilibrium is a strategy profile $$( \sigma )$$ where:

$$
u_1(\sigma) + \epsilon \geq \max_{ \sigma'_1 \in \Sigma_ 1} u_1(\sigma'_1, \sigma_ 2)
$$

$$
u_2(\sigma) + \epsilon \geq \max_{ \sigma'_2 \in \Sigma_ 2} u_2(\sigma_ 1, \sigma'_2)
$$

## Regret Minimization

When repeatedly playing an extensive game, let $$( \sigma^t_i )$$ be player \( i \)'s strategy in round \( t \). The average regret for player \( i \) at time \( T \) is:

$$
R^T_i = \frac{1}{T} \max_{\sigma^*_i \in \Sigma_i} \sum_{t=1}^{T} \left( u_i(\sigma^*_i, \sigma_{-i}^t) - u_i(\sigma^t_i) \right)
$$

The average strategy \( \bar{\sigma}^t_i \) from time 1 to \( T \) for each information set \( I \in I_i \) is defined as:

$$
\bar{\sigma}^t_i(I)(a) = \frac{\sum_{t=1}^{T} \pi_{\sigma^t_i}(I) \sigma^t(I)(a)}{\sum_{t=1}^{T} \pi_{\sigma^t_i}(I)}
$$

There is a well-known connection between regret and the Nash equilibrium solution concept.

#### Theorem
In a zero-sum game at time \( T \), if both players’ average overall regret is less than $$( \epsilon )$$, then strategy - $$( \bar{\sigma}^T )$$ is a $$( 2\epsilon)-equilibrium.$$

## Counterfactual Regret

The counterfactual regret minimization (CFR) algorithm is a regret minimization algorithm that has been shown to converge to a Nash equilibrium in two-player zero-sum extensive games with perfect recall.

The fundamental idea of our approach is to decompose overall regret into a set of additive regret terms, which can be minimized independently.

They show that overall regret is bounded by the sum of counterfactual regret, and also show how counterfactual regret can be minimized at each information set independently.


**Counterfactual utility** $$( u_i(\sigma, I) \) is the expected utility for player \( i \) if all players use strategy \( \sigma \), but player \( i \) specifically aims to reach information set \( I .$$
note - utility is defined as the expected value of the game outcome.

For a given information set \( I \) and player \( i \)'s choices, we define \( u_i(\sigma, h) \) as the expected utility given history \( h \).

The immediate counterfactual regret is defined as:

$$
R^T_{i,\text{imm}}(I) = \frac{1}{T} \max_{a \in A(I)} \sum_{t=1}^{T} \pi^ {\sigma ^t}_{-i}(I) \left( u_i(\sigma^t|_{I \to a}, I) - u_i(\sigma^t, I) \right)
$$

This reflects player \( i \)’s regret in decisions at \( I \) based on counterfactual utility, weighted by the probability of reaching \( I \). We focus on the positive portion of immediate counterfactual regret, defined as $$( R^T_{i,+,\text{imm}}(I) = \max(R^T_{i,\text{imm}}(I), 0))$$.

### key results of the paper

- Minimizing immediate counterfactual regret directly reduces overall regret, allowing us to find an approximate Nash equilibrium.

- This approach, similar to Gordon’s Lagrangian Hedging algorithms, avoids costly quadratic program projections while computing a Nash equilibrium in self-play.

## Conclusion

The paper introduces counterfactual regret as a novel concept for extensive games and demonstrates that minimizing counterfactual regret also minimizes overall regret.

It presents both a general and poker-specific algorithm for efficiently minimizing this regret.

The technique is applied in the domain of poker, achieving approximate equilibrium for abstractions with up to 10^12 states, significantly larger than previous methods.
