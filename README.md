# Monte-Carlo-Simulation
Run Monte Carlo Simulation 
This project runs Monte Carlo Simulation of Binomial Distribution, Poisson Distribution , Exponential Distribution, Multinomial Distribution ,Normal Distribution. Then it would calculate the number of t-statistic, Bootstrap statistic and randomized versions of t-statistic and Bootstrap statistic less than 95% percentile z-statistic of a standard normal distribution to see whether that number is around 0.95 or not. If it is approximately 0.95 that means the central limit theorem is supported by the simulation. 

 ```set.seed (123)```
 
```library("plyr")```

```N<-1000```

```z<-1.644854```

Create a distribution of t-statistic of 1000 samples of 20 observation from Binomial distribution Bin(10,0.1)

```n<-20```

```tstat_MC<-replicate(n=1000,expr={x=rbinom(20,10,0.1);c((mean(x)-1)/(sqrt(var(x))/sqrt(n)))})```

And calculate the number of t-statistic lessthan z-statistic = 1.644854

```count(tstat_MC<=z)```

Result: 965 => p=0.965

Create a distribution of t-statistic of 1000 samples of 20 observation from Poisson distribution Poi(1)

```n<-20```

```tstat_MC<-replicate(n=1000,expr={x=rpois(20,1);c((mean(x)-1))/(sqrt(var(x))/sqrt(n))})```

```count(Tn_MC<=z)```

Result: 960 (constant) => p=0.96

Create a distribution of t-statistic of 1000 samples of 20 observation from Exponential distribution Exp(1)

```n<-20```

```tstat_MC<-replicate(n=1000,expr={x=rexp(20);c((mean(x)-1))/(sqrt(var(x))/sqrt(n))})```

```count(Tn_MC<=z)```

Result: 960 (constant) => p = 0.96

Create a distribution of t-statistic of 1000 samples of 20 observation from Normal distribution Normal(2,9)

```n<-20```

```tstat_MC<-replicate(n=1000,expr={x=rnorm(20,2,3);c((mean(x)-2))/(sqrt(var(x))/sqrt(n))})```

```count(Tn_MC<=z)```

Result: 960 (constant) => p = 0.96

Create a distribution of randomized version of t-statistic of 1000 samples of 20 observation from Binomial distribution Bin(10,0.1)

```n<-20```

```a=rep(0,n)```

```b=rep(0,n)```

```vec.prob<-c(rep(1/n,n))```


```tstat_random_MC<-replicate(n=1000,expr={w=rmultinom(1,n,vec.prob);X=rbinom(20,10,0.1);for ( i in 1:n){
  a[i]<- abs(w[i]-1)*(X[i]-1)
  b[i]<-(w[i]-1)^2};
c(sum(a)/(sqrt(var(X))*sqrt(sum(b))))})```

count(tstat_random_MC<=z)

Result: 955 => p=0.955

Create a distribution of randomized version of t-statistic of 1000 samples of 20 observation from Poisson distribution Poi(1)

n<-20

vec.prob<-c(rep(1/n,n))

a=rep(0,n)

b=rep(0,n)

tstat_random_MC<-replicate(n=1000,expr={w=rmultinom(1,n,vec.prob);X=rpois(20,1);for ( i in 1:n){
  a[i]<- abs(w[i]-1)*(X[i]-1)
  b[i]<-(w[i]-1)^2};
c(sum(a)/(sqrt(var(X))*sqrt(sum(b))))})

count(tstat_random_MC<=z)

Result: 966 => p =0.966







