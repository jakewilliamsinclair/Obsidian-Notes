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