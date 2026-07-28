# Tanh (Hyperbolic Tangent)

A function that transforms real numbers into a value within the range (-1, 1).

## Formula

$$\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$$

Where:
1. $e$ = Euler's Number (2.71...)
2. $x$ = the input

## Understanding the formula

### Positive Values

When $x$ is positive, $e^x$ grows fast and $e^{-x}$ becomes small. So the numerator ($e^x - e^{-x}$) ends up almost equal to the denominator ($e^x + e^{-x}$), and the result approaches **1**.

Example with $x = 2$:

$e^2 \approx 7.389$ and $e^{-2} \approx 0.135$

$$\tanh(2) = \frac{7.389 - 0.135}{7.389 + 0.135} = \frac{7.254}{7.524} \approx \mathbf{0.964}$$

> So for positive values the result tends to get close to **1**.

### Negative Values

When $x$ is negative, the opposite happens: $e^{-x}$ grows and $e^x$ becomes small. The numerator becomes negative and nearly equal in magnitude to the denominator, so the result approaches **-1**.

Example with $x = -2$ (by symmetry, $\tanh(-x) = -\tanh(x)$):

$$\tanh(-2) \approx \mathbf{-0.964}$$

> So for negative values the result tends to get close to **-1**.

**Key difference from sigmoid:** tanh is zero-centered (range -1 to 1), while sigmoid ranges from 0 to 1. This matters because zero-centered outputs help gradient descent converge faster — the weights aren't all pushed in the same direction during backprop.

## Derivative

$$\tanh'(x) = 1 - \tanh^2(x)$$

Notice this derivative uses tanh's own result, just like sigmoid uses $\sigma(x)$.

Using $x = 2$, where $\tanh(2) \approx 0.964$:

$$\tanh'(2) = 1 - (0.964)^2 = 1 - 0.929 \approx \mathbf{0.071}$$

The signal (gradient) coming out is $0.071$, compared to the input signal. That means the gradient lost about 93% of the signal — you can already see the beginning of *vanishing gradient*, and it gets worse the further $x$ moves away from zero.

## Analysis

### 1. For $x = 10$

#### A. Calculate $\tanh(10)$:

$e^{10} \approx 22026.46$ and $e^{-10} \approx 0.0000454$

$$\tanh(10) = \frac{22026.46 - 0.0000454}{22026.46 + 0.0000454} \approx \mathbf{0.9999999958}$$

#### B. Calculate the derivative $\tanh'(10)$:

$$\tanh'(10) = 1 - (0.9999999958)^2 \approx \mathbf{0.0000000082}$$

The gradient practically vanishes. Almost 100% of the signal is lost.

---

### 2. For $x = -10$

#### A. Calculate $\tanh(-10)$:

By symmetry (odd function):

$$\tanh(-10) \approx \mathbf{-0.9999999958}$$

#### B. Calculate the derivative $\tanh'(-10)$:

Since the formula squares $\tanh(x)$, the negative sign disappears:

$$\tanh'(-10) = 1 - (-0.9999999958)^2 \approx \mathbf{0.0000000082}$$

Same result as for $x = 10$ — the gradient leaks equally on both sides.

---

**So from this we can understand a few things:**

1. If the values of $x$ are POSITIVE (+), the output tends to get close to **1**. If they are NEGATIVE (-), the output tends to get close to **-1**. (Unlike sigmoid, here the range is symmetric around zero.)
2. Large values of $x$, regardless of being POSITIVE or NEGATIVE, produce small gradients (vanishing gradient). Small values of $x$ — especially close to zero — produce the largest gradients, with the **maximum at $x = 0$, where $\tanh'(0) = 1$**.
3. Tanh suffers from the same saturation problem as sigmoid at the extremes, but because it's zero-centered, it generally converges better than sigmoid in practice — even so, very deep networks still prefer ReLU precisely to avoid this saturation.