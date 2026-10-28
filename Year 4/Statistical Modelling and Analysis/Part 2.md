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
## LSE
$\sum(X_{i}-\E(X))^2$ 
Sum of the difference between X values and the expected value, squared.
## MML
Calculate outcomes and choose highest probability.
### Example 6.12
You are given a coin that you do not think is fair (1/4 rather than 1/2). You flip the coin 10 times and observe that the number of head is 4.
Calculate probability of 4 heads out of 10 for each possibility:
Fair coin $X\sim Bin(10,0.5)$:
$\P(X=4)=\left(10\atop 4\right)(0.5)^4(1-0.5)^6=0.205$
Biased coin $X\sim Bin(10,0.25)$:
$\P(X=4)=\left(10\atop 4\right)(0.25)^4(1-0.25)^6-0.146$ 
$L(\theta,x)=f(x;\theta)$  $[pdf/pmf]$ 
### Likelihood function
For a paramater $\theta$, given a sample $x$:
$L(\theta,x)=f_{X}(x_{1};\theta)f_{X}(x_{2};\theta)\dots f_{X}(x_{n};\theta)=$ 
$\Pi_{i=1}^{n}f(x_{i};\theta)$ 
### Log-likelihood function:
$l(\theta)=l(\theta;x)=\ln[L(\theta,x)]=$ 
$\sum_{i=1}^{n}\ln(f(x_{i};\theta))$ 
### Score function:
$U(\theta)=U(\theta;x)=\frac{dl(\theta)}{d\theta}$ 
### Fisher's Information
$I(\theta)=\E\left[\left(\frac{dl}{d\theta}\right)^2\right]$ 
## MLE
The value of $\hat\theta$ that maximises $L(\theta)$. In many cases it is easier to maximise $l(\theta)$ which provides the same value for $\theta$.
$\frac{d}{d\theta}(\ln \theta)=\frac{1}{\theta}$ 
In general for $X\sim Bin(n,\theta)$ 
$L(\theta,x)=\left(n\atop x\right)\theta^x(1-\theta)^{n-x},l(\theta)=$ 
$k+x\ln(\theta)+(n-x)\ln(1-\theta)$ 

### Poisson:
$f(x_{i};\lambda)=\frac{e^{-\lambda}\lambda^{x_{i}}}{x_{i}!}$ 
$l_{i}(\lambda)=\ln\left(\frac{e^{-\lambda}\lambda^{x_{i}}}{x_{i}!}\right)$ 
$=-\lambda+x_{i}\ln(\lambda)-\ln(x_{i}!)$
So $l(\lambda)=\sum_{i=1}^n\{-\lambda+x_{i}\ln(\lambda)-\ln(x_{i}!)\}$ 
$=-n\lambda+(\ln(\lambda))\left(\sum_{i=1}^nx_{i}\right)-k$ 
$\implies \frac{dl}{d\lambda}=-n+\frac{\sum_{x=i}^nx_{i}}{\lambda}$ 
Set $\frac{dl}{d\lambda}=0$, solve for $\lambda$, find $\hat\lambda=\bar x$.
### Binomial
?#######
## Classical large samples properties of MLEs
In large samples, an MLE $\hat\theta$ is approximately unbiased, efficient and normally distributed.
So asymptotically
$\hat\theta \sim N\left(\theta,\frac{1}{I(\theta)}\right)$ 
So asymptotically,
$se\left( \hat{\theta}=\frac{1}{\sqrt{I(\theta)}} \right)$ 
estimate standard error by:
$ese(\hat{\theta})=\frac{1}{\sqrt{ I(\hat{\theta}) }}$ 