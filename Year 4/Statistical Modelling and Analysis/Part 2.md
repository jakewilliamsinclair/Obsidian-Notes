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
The bias of $\hat{\theta}$ is $B(\hat{\theta}) = E(\hat{\theta} - \theta) = E(\hat{\theta}) - \theta$ 

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
$\E[X]$ roughly equals $\bar{X}$ so for some $\theta=f(\E[X])$ it holds $\hat{\theta}=f(\bar{X})$ 
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
Or (somehow)
$I(\theta)=-\E\left[\frac{d^2l}{d\theta^2}\right]$ 
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
## MLEs in multi-parameter models
$\frac{\partial l}{\partial \mu}=2\sum \left(\frac{X_{i}-\mu}{2\phi}\right)$ 
# Confidence Interavals
$\P(L_{1}\le \theta \le L_{2})\ge 1-\alpha$ 
Choose $\alpha$, e.g. $\alpha=0.05$ 
Then calculate $L_{1},L_{2}$ 
## CI's for Population Mean
Suppose $X\sim N(\mu,\sigma^2)$ 
### $\sigma^2$ Known
Start here:
$\P\left(-1.9600\lt Z\lt 1.9600\right)=0.95$ (from table 5)
Z is standardised, un-standardise for X
$\P\left(-1.9600\lt \frac{\bar{X}-\mu}{{\sigma}/{\sqrt{ n }}} \lt 1.9600\right)$ 
Move things around to get $\mu$ alone
$\P\left( -1.96 \frac{\sigma}{\sqrt{ n }} \lt \bar{X}-\mu \lt 1.96 \frac{\sigma}{\sqrt{ n }}\right)$ 
$\P\left(-\bar{X}-1.96 \frac{\sigma}{\sqrt{ n }}\lt -\mu \lt \bar{X}-\bar{X}+1.96 \frac{\sigma}{\sqrt{ n }}\right)$ 
$\P\left(\bar{X}-1.96 \frac{\sigma}{\sqrt{ n }} \lt \mu \lt \bar{X} + 1.96 \frac{\sigma}{\sqrt{ n }} \right)$ 
95% CI for $\mu$ is $\bar{X}\pm 1.96 \frac{\sigma}{\sqrt{ n }}$ 
This can be generalised by:
$X\pm z\times \frac{\sigma}{\sqrt{ n }}$ where $z$ is the value from the tables (half the 5% -> 2.5% and get that value).
### $\sigma^2$ Unknown
Must use estimated standard error e.s.e
$e.s.e(\bar{X})=\frac{S}{\sqrt{ n }}$ 
#### Example 7.7
Random sample of 20 observations from $N(\mu, \sigma^2)$ 
$$
\bar{x}=\frac{4035}{20}=201.75\\
s^2=\frac{1}{n-1}\left(\sum x_{i}^2-\frac{\left(\sum x_{i}\right)}{n}\right)\\
=\frac{1}{19}\left(857115-\frac{4025^2}{20}\right)\\
=2265.99
$$
With $n=20$, for 95% two-sided CI, need $\P(t_{19}\gt t)=0.025$ 
Table 10 => $t=2.039$ 
formula of sample mean times standard error (from formula sheet)
95% CI is $\bar{x}\pm 2.093\times \frac{s}{\sqrt{ n }}$ 
$=201.75\pm 2.093\times \sqrt{ \frac{2265.99}{20} }$ 
$=(179.47, 224.03)$ (lower, upper)
### Large Sample
This means that even though we may not know $\sigma$ we can assume we have a reasonable estimate as the sample is large (CLT style).
$e.s.e(\bar{x})=\frac{s}{\sqrt{ n }}$ 
Only use t-table if data is normally distributed.
### One Sided Interval
$\P\left(\frac{\bar{X}-\mu}{\sigma/\sqrt{ n }}\lt 1.645\right)=0.95$ 
this gives
$\left( \bar{X}-1.645 \frac{\sigma}{\sqrt{ n }},\infty \right)$ 
## CIs for Population Variace
$X\sim N(\mu,\sigma^2)$, we want CI for $\sigma^2$.
$\P(X\lt a)=\P(X \gt b) = \frac{\alpha}{2}$ 
Then we have
$\P\left(a \lt \frac{(n-1)S^2}{\sigma^2} \lt b\right)=1-\alpha$ 
becomes
$\P\left(\frac{(n-1)S^2}{b} \lt \sigma^2 \lt \frac{(n-1)S^2}{a}\right)$ 
$\left(\frac{(n-1)S^2}{b}, \frac{(n-1)S^2}{a}\right)$ 
This is on the formula sheet
Back to
### Example 7.7
With $n=20$, for 95% CI for $\sigma^2$, need
$\P(\chi_{19}^2\lt a)=0.025\implies a=8.907$ 
$\P(\chi_{19}^2\lt b)=0.025\implies b=32.85$ 
CI is $\left(\frac{(n-1)S^2}{b},\frac{(n-1)S^2}{a}\right)=\left(\frac{19\times 2265.99}{32.85}, \frac{19\times 2265.99}{8.907}\right)$ 
$=(1310.62, 4833.70)$ 
95% CI for $\sigma$ is $\left(\sqrt{ 1310.62 }, \sqrt{ 4833.70 }\right)$
$=(36.20,69.52)$ 

New data:
$n=19$ 
$\sum x_{i}=4035-359=3676$ 
$\sum x_{i}=837115-359^2=728234$ 
95% CIs for $\mu$ & $\sigma$ ... exercise for me
## CIs for Population Proportion
$X\sim Bin(n,\theta)$ where $\theta$ is the probability of success but $P=\frac{X}{n}$ or observed probability of success $(\frac{successes}{trials})$ can also be referred to as $\hat{\theta}$.
$P\pm \left( z_{\frac{a}{s}}\times ese(P)) \right)$ 
where
$ese(P)=\sqrt{ \frac{P(1-P)}{n} }$ 
### Example 7.8
Calculate 95% CIs for $\theta$
a) a random sample of 200 includes 70 with the property:
b) a random sample of 1200 includes 420 with the property:
a) $\hat{\theta}=\frac{70}{200}=0.35,n=200$ 
$ese(\hat{\theta})=\sqrt{ \frac{0.25\times 0.65}{200} }=0.0337$ 
$0.35\pm 1.96\times 0.0337$ 
$=(0.2840.416)$ 

b) $\hat{\theta}=\frac{420}{1200}=0.35,n=1200$ 
$ese(\hat{\theta})=\sqrt{ \frac{0.25\times 0.65}{1200} }=0.0138$ 
$0.35\pm 1.96\times 0.0138$ 
$=0.35\pm 0.027048$ 
$=(0.323,0.377)$ 
## CIs for Poisson Mean
$\bar{X}\pm$ Formula sheet
### Example 7.3
Number of potholes in a month is Poisson with mean $\lambda$.
Total number of holes in 36 months is 442. Find CI for $\lambda$.
$n=36, \hat{\lambda}=\frac{442}{36}=12.278$ 
$ese(\hat{\lambda})=\sqrt{ \frac{\hat{\lambda}}{n} }=\sqrt{ \frac{12.278}{36} }=0.584$  
95% CI for $\lambda$ is $12.278\pm 1.96\times 0.584$ 
$=12.278\pm 1.145$ 
$=(11.13,13.42)$ 

99% CI for $\lambda$ is (just to compare)
requires a different critical value from the table
$12.278\pm 2.5758\times 0.584$ 
$=12.278\pm 1.504$ 
$=(10.77,13.78)$ 
We can see the 99% CI is wider than the 95% CI.

## CIs Based on General MLEs
For large sample MLEs we have a useful simple result based on the normal distribution.
In many cases an MLE $\hat{\theta}$ is approx. $N\left( \theta, \frac{1}{I(\theta)} \right)$ 

$\hat{\theta}\pm\left( z_{\frac{\alpha}{2}}\times se(\hat{\theta}) \right)$ 
MEMORISE THIS:
$ese(\hat{\theta})=\sqrt{ \frac{1}{I(\theta)} }$ 

### Example 7.4
Random sample size n, of $X\sim Exp(\lambda)$ (so mean $\mu=\frac{1}{\lambda}$)
Construct an **approximate** (this word means use normal distribution) 95% CI for $\lambda$.