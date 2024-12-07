---
layout: post
title: 'Probabilistic Analysis of Gossip Protocols: Ensuring Reliable Message Dissemination'
author: "Vipul Vaibhaw"
---

## Setup and Binomial Model

### Setup
Consider a network of $N$ nodes. Initially, only the leader is informed, and it starts the gossip. In each round $t$, each informed node sends a message to $k$ randomly chosen neighbors, attempting to spread the message. Let $I_t$ be the number of informed nodes and $U_t = N - I_t$ the number of uninformed nodes at the start of round $t$. Another assumption is that the message size is small enough to be delivered in a single request.

### Binomial Model
The number of newly informed nodes in round $t$, $X_t$, follows a binomial distribution:

$$
X_t \sim \text{Binomial}(n, p), \quad \text{where } p = \frac{U_t}{N}.
$$

Here, $n$ is the total number of gossip attempts, and $p$ is the probability of selecting an uninformed node.

---

## Poisson Approximation and Failure Probability

### Poisson Approximation
For large $n$ and small $p$, the binomial distribution can be approximated by a Poisson distribution with parameter:

$$
\lambda = n \cdot \frac{U_t}{N}.
$$

Thus, $X_t$ can be written as:

$$
X_t \sim \text{Poisson}(\lambda).
$$

### Failure Probability
Using the Poisson probability mass function (PMF), the probability of no new nodes being informed in round $t$ is:

$$
P(X_t = 0) = e^{-\lambda}.
$$

The probability that a specific node remains uninformed after $n$ rounds is:

$$
P(\text{Failure after $n$ rounds}) = \prod_{t=1}^n e^{-\lambda_t} = e^{-\sum_{t=1}^n \lambda_t}.
$$

### Cumulative Success
The expected number of informed nodes after $n$ rounds is:

$$
E[\text{Informed Nodes}] = N \cdot \left(1 - e^{-\lambda \cdot n}\right).
$$

For $n > 10$, $e^{-\lambda \cdot n}$ becomes negligible, meaning nearly all nodes are informed.

---

## Conclusion

By modeling the gossip protocol as a binomial process and approximating it with a Poisson distribution, we see that the failure probability decreases exponentially with the number of rounds. For $n > 10$, the probability of a node remaining uninformed drops below $0.05$, ensuring reliable message dissemination. The result is independent of $k$ (the number of nodes chosen for gossip) or the total size of the cluster.
