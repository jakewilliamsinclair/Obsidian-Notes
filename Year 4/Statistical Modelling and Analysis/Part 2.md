$\newcommand{\P}{\mathbb{P}}\newcommand{\E}{\mathbb{E}}$
# Methods of Estimation
Statistics are information that can be gained **from** data. For example the sample variance is found from the data itself but $\mu$ cannot be found from the data so it is not a statistic.

An **estimator** of $\theta$ is statistic whose value is used as an estimate of $\theta$.
We denote the estimator $\hat{\theta}$ (can also be written $\tilde\theta, \theta^*$).
For example
$\hat\theta = \frac{1}{n}\sum_{i=1}^{n}X_{i}$ 
$\hat\theta = \sum_{i=1}^{n}\omega_{i}X_{i}$ where $\omega$ are known constants
are both reasonable estimators ($\omega$ would reasonably be chosen as $\frac{1}{n}$ anyway).

$\hat\theta$ is asymptotically unbiased for $\theta$ if $\E(\hat\theta) = \theta$ 
The bias of ˆθ is B(ˆθ) = E(ˆθ − θ) = E(ˆθ) − θ

The mean square error of an estimator $\hat\theta$ is MSE($\hat\theta$) = $\E[(\hat\theta − \theta)^2]$.
An estimator $\hat\theta_{1}$ is more efficient than $\hat\theta_2$ if $MSE[\hat\theta_{1}]\lt MSE[\hat\theta_{2}]$.
## Consistency
An estimator $\hat\theta$ is consistent for $\theta$ if, for any $\epsilon\lt 0$
$\P(|\hat\theta-\theta|\ge\epsilon)\to 0$ as $n\to\infty$
### Examples
$\bar{X}$ is unbiased for $\mu$ with variance $\frac{\sigma^2}{n}\to 0$ as $n\to\infty$ so $\bar{X}$ is consistent for $\mu$.
Sampling from $X\sim N(\mu,\sigma^2)$. We have
$\frac{(n-1)S^2}{\sigma^2}\sim X_{n-1}^{2}$ so $V(S^2)=\frac{2\sigma^4}{n-1}$ 

### Sufficiency
An estimator $\hat\theta$ is sufficient for $\theta$ if the conditional distributions of $X$ given $\hat\theta$ does not depend on $\theta$.
A sufficient statistic contains all the information in the data relevant to estimating $\theta$. There is 'factorisation criterion' for establishing sufficiency.
For example the order of heads and tails is (typically) irrelevant so does not need to be recorded.
# Methods of Constructing Estimators
1. Methods of moments estimators (MME)
2. Method of least squares estimators (LSE)
3. Maximum likelihood estimators (MLE)
## MME
Equate population mean and variance to corresponding sample means and variance.
### Example 6.20
Random sample, size 5, $X\sim U(0,\theta)$.
Data $x=(0.46,1.14,0.83,0.21,0.59)$
To find MME:
$\E(X)=\frac{\theta}{2}$ (from uniform definition)
So $\bar{X}=\frac{\hat\theta}{2}$ 
$\implies \hat\theta=2\bar{X}$ is MME
With given data, $\bar{x}=0.646$, so $\hat\theta=1.292$
Unbiased? $\E(\hat\theta)=\E(2\bar{X})$
$=2\E(\bar{X})$
$=2\E(X)$
$=2\times \frac{\theta}{2}$ 