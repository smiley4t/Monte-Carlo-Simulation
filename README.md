# Monte-Carlo-Simulation
Run Monte Carlo Simulation 
This project runs Monte Carlo Simulation of Binomial Distribution, Poisson Distribution , Exponential Distribution, Multinomial Distribution ,Normal Distribution. Then the results would compare t-statistic, Bootstrap statistic and randomized versions of t-statistic and Bootstrap statistic with 95% percentile z-statistic of a standard normal distribution to see whether it fits the theology.

 ```set.seed (123)```
 
```library("plyr")```

```N<-1000```

```z<-1.644854```

Create a distribution of t-statistic of 1000 samples of 20 observation from Binomial distribution Bin(10,0.1)

```n<-20
tstat_MC<-replicate(n=1000,expr={x=rbinom(20,10,0.1);c((mean(x)-1)/(sqrt(var(x))/sqrt(n)))})
count(tstat_MC<=z)```

##965 => p=0.965

##Create a distribution of t-statistic of 1000 samples of 20 observation from Poisson distribution Poi(1)

```n<-20
tstat_MC<-replicate(n=1000,expr={x=rpois(20,1);c((mean(x)-1))/(sqrt(var(x))/sqrt(n))})
count(Tn_MC<=z)```

##960 (c0nstant) => p=0.96
