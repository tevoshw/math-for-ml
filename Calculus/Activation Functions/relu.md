# ReLU (Rectified Linear Unit)

The most widely used activation in deep networks. Fixes the vanishing gradient problem seen in sigmoid/tanh.

## Formula

$$\text{ReLU}(x) = \max(0, x)$$

- If $x > 0$: returns $x$ itself
- If $x \leq 0$: returns $0$

No exponentials, no division — just a cutoff.

## Examples

$$\text{ReLU}(5) = 5$$
$$\text{ReLU}(-3) = 0$$
$$\text{ReLU}(0) = 0$$

## Derivative

$$\text{ReLU}'(x) = \begin{cases} 1 & \text{if } x > 0 \\ 0 & \text{if } x < 0 \end{cases}$$

(At $x = 0$ the derivative is technically undefined; frameworks like PyTorch/TensorFlow just pick 0 or 1 by convention.)

## Maximum value of the derivative

Max is **1**, and it's constant — no saturation like sigmoid/tanh. For any $x > 0$, the gradient passing through is always exactly 1, no matter how large $x$ gets. Signal flows through positive activations at full strength.

## The catch: "dying ReLU"

If $x \leq 0$, the derivative is **0** — the gradient dies completely there. If a neuron gets stuck always receiving negative inputs, it stops learning forever (weights never update again). This differs from sigmoid/tanh saturation (small but nonzero gradient) — here the gradient is **exactly zero**.

> This is why variants like Leaky ReLU, PReLU, and ELU exist — they give a small gradient for negative values too, preventing neurons from fully "dying."