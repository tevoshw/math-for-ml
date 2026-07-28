# Sigmoid
A function that transform real numbers at a value within the range (0, 1).

## Formula

. $$\sigma(x) = \frac{1}{1 + e^{-x}}$$ 

Wheres:
1. $e$ = Eulers Numbers (2.71....)
2. $x$ = the input


## Understand the formula


### Positive Values
When the $x$ value it's positive, the expoent are NEGATIVE for default, so:

$y^{-x}$ = $\frac{1}{y^{x}}$

And the value of this gonna be a small number:
$\frac{1}{2^{3}}$ = $\frac{1}{8}$ = $0.125$ and add this in the formula $$\frac{1}{1 + 0.125} =  0.8$$  

> So for positive values gonna be a big number (0.8)

### Negative Values
When the $x$ value it's negative, the expoent are POSITIVE for default, so:

$y^{-(-x)}$ = $y^{+x}$

And the value of this gonna be a big number:
$2^{+4} = 16$

So put in the frac

. $$\frac{1}{1 + 16} =  0.05$$ 



> So for negatives values gonna be a small number (0.05)

## Derivate

$$\sigma'(x) = \sigma(x) \cdot (1 - \sigma(x))$$

So for  $e$ = 2, $x$ = 3, the $\sigma(x) = 0.8$ 

. $$\sigma'(x) = 0.8 \cdot (1 - 0.8) = 0.16 $$ 

So the result (signal) are $0.16$, compared to the signal that enters $3$. That's means the gradient missed about 84% of the signal that arrived (activation) CAUSING A VANISH GRADIENT

> So using the sigmoid function can cause vanishing gradient for this math explanation

## Analyses

### 1. For $x = 10$

#### A. Calculate the Sigmoide $\sigma(10)$:
$$\sigma(10) = \frac{1}{1 + e^{-10}}$$

 $e^{-10} \approx 0.0000454$:

$$\sigma(10) = \frac{1}{1 + 0.0000454} = \frac{1}{1.0000454} \approx \mathbf{0.99995}$$

#### B. Calculate the Derivate $\sigma'(10)$:
Usando a fórmula da derivada $\sigma'(x) = \sigma(x) \cdot (1 - \sigma(x))$:

$$\sigma'(10) = 0.99995 \cdot (1 - 0.99995)$$

$$\sigma'(10) = 0.99995 \cdot 0.00005 \approx \mathbf{0.00005}$$

---

### 2.  $x = -10$

#### A. Calculate the Sigmoide $\sigma(-10)$:
$$\sigma(-10) = \frac{1}{1 + e^{-(-10)}} = \frac{1}{1 + e^{10}}$$

$e^{10} \approx 22026.46$:

$$\sigma(-10) = \frac{1}{1 + 22026.46} = \frac{1}{22027.46} \approx \mathbf{0.0000454}$$

#### B. Calculate the Derivate $\sigma'(-10)$:
Usando a fórmula da derivada:

$$\sigma'(-10) = 0.0000454 \cdot (1 - 0.0000454)$$

$$\sigma'(-10) = 0.0000454 \cdot 0.9999546 \approx \mathbf{0.0000454}$$

**So after that we can understand some thing like**
1. If the values of X are POSITIVE (+) the output gonna be nearest to 1. Else are NEGATIVE (-) the output gonna be nearest to 0
2. Big values for X independent of being POSITIVE or NEGATIVE gonna have the small number for gradient. WHILE small values for X gonna have the biggest numbers for gradients (in this context)