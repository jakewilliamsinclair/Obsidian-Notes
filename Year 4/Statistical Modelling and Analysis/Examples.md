# Example 5.16
A computer simulation program selects six random numbers independently and at random from the interval (0,5).
Random numbers are $U(5)$ 
$X\sim \left( 6,\frac{2}{5} \right)$ 

# Example 5.17
Suppose the length of times between failures of generators at a dam have an exponential distribution. The average time, as measured by the median, is 624 minutes.
• What is the average times as measured by the mean?
• What percentage of times are greater than 1000 minutes ?

$X\sim Exp(\lambda)$ has c.d.f. $\P(X\leq x)=F(x)=1-e^{-\lambda x}$ 
Median = 624, so
$F(624)=\frac{1}{2}$
$1-e^{-624x}=\frac{1}{2}$
$-624x=\ln\left( \frac{1}{2} \right)=\lambda=\frac{\ln\left( \frac{1}{2} \right)}{-624}$ 

$n=\frac{1}{\lambda}=900.24$ minutes

# Example 5.22
Random sample of 200 observations, mean 35, variance 16.
$n=200, \mu=35, \sigma^{2}=16$
As we have a large sample size, we can apply CLT:
$\bar{X}\sim N\left( 35, \frac{16}{200} \right)$ approximately

# Example 6.21
Random sample, size $n$, of a random variable $X$ with probability density function
$f(x)=2\theta e^{(-\theta x^2)},x\gt 0$ 
a) Find MME of $\theta$ 
$\E(X)=\frac{\sqrt{ \pi/\theta }}{2}=\bar{X}$ 
$\to \hat{\theta}=\frac{\pi}{4x^{-2}}$ 
b) Find the MLE of $\theta$, the score function $U(\theta)$ and Fisher's information function $I(\theta)$. State the asymptotic distribution of the MLE.
$L(\theta)[\P(x|\theta)]=$ 
$\Pi_{i=1}^nf(x_{i}|\theta)=\Pi_{i=1}^{n} 2\theta x_{i}e^{-\theta x_{i}^2}$ 

$L(\theta)=l(\theta)$ 
$\ln(L(\theta))=\ln\left(\Pi_{i=1}^{n} 2\theta x_{i}e^{-\theta x_{i}^2}\right)$ 
$l(\theta)=\sum \ln(2\theta x_{i}e^{-\theta x_{i}^2})$ 
$\sum(\ln 2+\ln \theta+\ln x_{i}+(-\theta x_{i}^2))$ 

$U(\theta)=\frac{d}{d\theta}l(\theta)=\sum\left( \frac{1}{\theta}-x_{i}^2 \right)$ 
$=\left( \frac{n}{\theta}-\sum x_{i}^2 \right)$ 

$U(\hat{\theta})=0\to \frac{n}{\theta}-\sum x_{i}^2=0$ 
$\to \hat{\theta}=\frac{n}{\sum x_{i}^2}$ 
$I(\theta)=\frac{-d}{d\theta}U(\theta)=\frac{-d}{d\theta}\left( \frac{n}{\theta}-\sum x_{i}^2 \right)$ 
$=\frac{n}{\theta^2}$ 
# Example 6.22
$X$ is the number of boys in families with 3 children.
$X=1\ |\ 2\ |\ 3\ |\ 4$
$\P(X=x)=\theta\ |\ \frac{3\theta}{2}\ |\ \frac{3\theta}{2}\ |\ 1-4\theta$ 
$0\le \P(X=x)\le 1$ 
$\theta\le 0.25$ 
In a random sample of 100 families, the numbers were as follows:
$x=0\ |\ 1\ |\ 2\ |\ 3$
$Families=18\ |\ 34\ |\ 26\ |\ 22$ 
a) Find the method of moments estimate of $theta$ 
$\E(x)=\sum P(X=x_{i})\times x_{i}$ 
$\frac{3\theta}{2}\times 1+\frac{3\theta}{2}\times 2+(1-4\theta)\times 3$ 
$\frac{3\theta}{2}+3\theta+3-12\theta$
$3-\frac{15\theta}{2}$
$\bar{x}=3-\frac{15\hat{\theta}}{2}$ 
$\hat{\theta}=\frac{2}{15}(3-\bar{x})$ 

$\bar{x}=\frac{0\times 18+1\times 34+2\times 26+3\times 22}{100}$
$=1.52$ 

$\hat{\theta}=\frac{2}{15}(3-1.52)=$ 
$\frac{2}{15}\times 1.5=0.2$ 

b) Find MLE
$L(\theta)\propto(\theta)^{18}\times\left( \frac{3\theta}{2} \right)^{34}\times\left( \frac{3\theta}{2} \right)^{26}\times(1-4\theta)^{22}$ 
$=18\log(\theta)+34\log\left( \frac{3\theta}{2} \right)+26\log\left( \frac{3\theta}{2} \right)+22\log(1-4\theta)$ 

$L(\theta)=\frac{d}{d\theta}l(\theta)$  
$60\log\left( \frac{3\theta}{2} \right)$
$=60\left( \log \frac{3}{2}+\log \theta \right)$ 
$l(\theta)=78\log(\theta)+60\log \frac{3}{2}+22\log(1-4\theta)$ 
$\frac{78}{\theta}-\frac{22\times 4}{1-4\theta}$ 
