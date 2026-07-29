# Derivatives

## What is a derivative?

A derivative measures how a function's output changes with respect to a small change in its input. It is the **instantaneous rate of change**, or equivalently, the **slope of the tangent line** to the function at a given point.

$$f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}$$

## Notation

- $f'(x)$ — Lagrange notation
- $\frac{dy}{dx}$ — Leibniz notation
- $\dot{y}$ — Newton notation (common in physics, time derivatives)
- $\frac{\partial f}{\partial x}$ — partial derivative (used when $f$ depends on multiple variables)

## Why derivatives matter

- **Optimization**: finding where a function is minimized or maximized (derivative = 0 at critical points)
- **Rates of change**: velocity is the derivative of position, acceleration is the derivative of velocity
- **Machine learning**: gradients (vectors of partial derivatives) drive gradient descent and backpropagation
- **Sensitivity analysis**: how much does output change if input changes slightly

## Key concepts

**Slope of a curve**: at any point, the derivative gives the slope of the line tangent to the curve at that point. A positive derivative means the function is increasing; negative means decreasing; zero means a flat point (local min, max, or saddle).

**Differentiability**: a function must be continuous and "smooth" (no sharp corners or breaks) at a point to be differentiable there.

**Higher-order derivatives**: the derivative of a derivative. The second derivative $f''(x)$ describes concavity (curvature) — positive means concave up, negative means concave down.

**Partial derivatives**: when a function has multiple inputs, the partial derivative $\frac{\partial f}{\partial x_i}$ measures the rate of change with respect to one variable, holding all others constant.

**Gradient**: the vector of all partial derivatives of a multivariable function, pointing in the direction of steepest increase. Central to optimization in machine learning.

## Chain rule (foundation of backpropagation)

If $y = f(g(x))$, then:

$$\frac{dy}{dx} = f'(g(x)) \cdot g'(x)$$

This is the mechanism that allows derivatives to be computed through compositions of functions — essential for differentiating deep neural networks layer by layer.

---

## Como Derivar Regras:

### 1. Constant rule

$$\frac{d}{dx}[c] = 0$$

The derivative of a constant is always zero. A constant never changes, so its rate of change is zero. Graphically, a horizontal line has zero slope everywhere.

### 2. Power rule

$$\frac{d}{dx}[x^n] = n \cdot x^{n-1}$$

Bring the exponent down as a multiplier, then subtract 1 from the exponent.

- $\frac{d}{dx}[x^3] = 3x^2$
- $\frac{d}{dx}[x] = 1$ (since $x = x^1$)
- $\frac{d}{dx}[\sqrt{x}] = \frac{d}{dx}[x^{1/2}] = \frac{1}{2}x^{-1/2} = \frac{1}{2\sqrt{x}}$
- $\frac{d}{dx}\left[\frac{1}{x}\right] = \frac{d}{dx}[x^{-1}] = -x^{-2} = -\frac{1}{x^2}$

### 3. Constant multiple rule

$$\frac{d}{dx}[c \cdot f(x)] = c \cdot f'(x)$$

A constant coefficient carries through the derivative unchanged.

$$\frac{d}{dx}[5x^3] = 5 \cdot 3x^2 = 15x^2$$

### 4. Sum and difference rule

$$\frac{d}{dx}[f(x) \pm g(x)] = f'(x) \pm g'(x)$$

Differentiate each term separately, then add or subtract the results.

$$\frac{d}{dx}[x^3 + x^2 - 4x] = 3x^2 + 2x - 4$$

### 5. Product rule

$$\frac{d}{dx}[f(x) \cdot g(x)] = f'(x)g(x) + f(x)g'(x)$$

Used when two functions of $x$ are multiplied together. "Derivative of the first times the second, plus the first times the derivative of the second."

$$\frac{d}{dx}[x^2 \cdot \sin(x)] = 2x\sin(x) + x^2\cos(x)$$

### 6. Quotient rule

$$\frac{d}{dx}\left[\frac{f(x)}{g(x)}\right] = \frac{f'(x)g(x) - f(x)g'(x)}{[g(x)]^2}$$

Used when dividing two functions. Numerator: "derivative of top times bottom, minus top times derivative of bottom." Denominator: bottom function squared.

$$\frac{d}{dx}\left[\frac{x^2}{x+1}\right] = \frac{2x(x+1) - x^2(1)}{(x+1)^2}$$

### 7. Chain rule

$$\frac{d}{dx}[f(g(x))] = f'(g(x)) \cdot g'(x)$$

Used for composite functions (a function inside another function). Differentiate the outer function first, keeping the inner function unchanged, then multiply by the derivative of the inner function.

$$\frac{d}{dx}[(x^2+1)^5] = 5(x^2+1)^4 \cdot 2x$$

This is the rule that makes backpropagation possible — it lets derivatives propagate through layers of composed functions.

### 8. Exponential rule

$$\frac{d}{dx}[e^x] = e^x$$

$$\frac{d}{dx}[a^x] = a^x \ln(a)$$

$e^x$ is the only function that is its own derivative — this is the defining property of $e$.

### 9. Logarithmic rule

$$\frac{d}{dx}[\ln(x)] = \frac{1}{x}$$

$$\frac{d}{dx}[\log_a(x)] = \frac{1}{x \ln(a)}$$

### 10. Trigonometric rules

$$\frac{d}{dx}[\sin(x)] = \cos(x)$$

$$\frac{d}{dx}[\cos(x)] = -\sin(x)$$

$$\frac{d}{dx}[\tan(x)] = \sec^2(x)$$

### Quick reference table

| Function | Derivative |
|---|---|
| $c$ | $0$ |
| $x^n$ | $n x^{n-1}$ |
| $e^x$ | $e^x$ |
| $a^x$ | $a^x \ln(a)$ |
| $\ln(x)$ | $\frac{1}{x}$ |
| $\sin(x)$ | $\cos(x)$ |
| $\cos(x)$ | $-\sin(x)$ |
| $\tan(x)$ | $\sec^2(x)$ |
| $f(x)\cdot g(x)$ | $f'g + fg'$ |
| $f(x)/g(x)$ | $\frac{f'g - fg'}{g^2}$ |
| $f(g(x))$ | $f'(g(x))\cdot g'(x)$ |