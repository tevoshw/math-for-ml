# Softmax

Transforms a vector of real numbers into a probability distribution (sums to 1).

## Formula

$$\text{softmax}(x_i) = \frac{e^{x_i}}{\sum_{j=1}^{n} e^{x_j}}$$

- $x_i$ = logit of element $i$
- Denominator = sum of exponentials of **all** logits (same value for every element)

## Key difference

Sigmoid/tanh look at a single number in isolation. Softmax looks at the **whole vector** — each output depends on all the others.

## Example (3 classes, logits = [2, 1, 0.1])

$e^2{\approx}7.389$, $e^1{\approx}2.718$, $e^{0.1}{\approx}1.105$ → sum = 11.212

$$s_1{\approx}0.659,\quad s_2{\approx}0.242,\quad s_3{\approx}0.099 \quad(\text{sum}=1)$$

## Special cases

**1 number:** always gives **1** (single class = 100% probability).

**2 numbers:** equivalent to sigmoid on the difference of the logits:
$$\text{softmax}(x_1) = \sigma(x_1 - x_2)$$

## Derivative (Jacobian)

$$\frac{\partial s_i}{\partial x_j} = s_i(\delta_{ij} - s_j)$$

- **$i=j$:** $s_i(1-s_i)$ → same as the sigmoid derivative
- **$i \neq j$:** $-s_i s_j$ → boosting one class pulls the others down (sum always = 1)

## Maximum value

$$s_i(1-s_i) \Rightarrow \max = 0.25 \text{ when } s_i = 0.5$$

Max gradient (0.25) happens when the class is uncertain (50%). Near 0 or 1 (high or low confidence), the gradient saturates — same issue seen in sigmoid and tanh.