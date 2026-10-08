[[Statistical Modelling and Analysis#Probability Mass Function|PMF]] $p_X(x)$ is specific value (only useful for discrete)
[[Statistical Modelling and Analysis#Cumulative Distribution Function|CDF]] $F_X(x)$ is chance of X being <= x

# Discrete PMF
$p_X(x)=f(X)=$ Chance that X is x
# Discrete CDF
$F_X(x)=\mathbb{P}(X\le x)=$ Chance that X is less than or equal to x
Add up all probabilities of X being a value less than or equal to x.
# Continuous PDF
(PMF for continuous)
$\mathbb{P}(x_1\le X\le x_2)=$ Chance that X takes a value between $x_1$ and $x_2$.
Calculate definite integral from $x_1$ to $x_2$ of $f_X(x)$.
# Continuous CDF
Same as discrete in meaning (X$\le$x)
$F_X(x)=$ Calculate integral from -$\infty$ to $x$ of $f_X(x)$.
# Expected Value
**Discrete** - Sum of the products of values and probabilities
$\mathbb{E}[X]=\sum{xp_X(x)}$ 
**Continuous** - 
$\mathbb{E}[X]=\displaystyle\int{xf_X(x)}dx$ 