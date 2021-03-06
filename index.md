---
title       : Skewed Normal Distributions
subtitle    : explaining some basics
author      : Hartwig Toedter
job         : Programmer
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
logo        : boss.jpg
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]     # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Theoretical background
Given a random variable $X$, which has the probability denisity function
$$f(x) = 2 \phi(x)\ \Phi(\alpha x)$$
where $\alpha$ is a number and
$$\phi(x)= \exp(-x^2/2)/\sqrt{2\pi} ,
   \qquad \Phi(\alpha x) = \int_{-\infty}^{\alpha  x}\phi(t)\,dt$$

Set $\begin{equation}Y \: =\: \xi\, +\, \omega\, X\end{equation}$ and $Y$ is said to 
have a skewed normal distribution with parameters $\xi$, $\omega$ and $\alpha$
$$Y\: \sim\:  SN(\xi,\,\omega^2,\,\alpha).$$

$\xi$ is called location, $\omega$ scale and $\alpha$ shape. 

---

## Characteristics of a skewed normal distribution

Let $Y$ be a random variable which has a skewed normal distribution
$$Y\: \sim\:  SN(\xi,\,\omega^2,\,\alpha).$$

The mean value of $Y$ is: $$E\{Y\} = \xi+\omega\:\sqrt{2/\pi}\,\delta$$

The variance of $Y$ is: $$VAR\{Y\}= \omega^2\;(1-2\,\delta^2/\pi)$$

Here $\delta$ ist defined as: $\delta=\alpha/\sqrt{1+\alpha^2}$

From this it can easily be seen that for $\alpha = 0$ $Y$ symetric normal distributed:
$$Y\: \sim\: N(\xi,\,\omega^2)$$

--- &twocol w1:40% w2:60%

## Example of a right skewed distribution

*** {name: left}



![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2-1.png)

*** {name: right}


```r
library(sn)
location = 0
scale = 1
shape = 4

set.seed(1234)
data = rsn(1000, xi=location, omega=scale, 
           alpha = shape)
hist(data, breaks=20, probability=TRUE, 
   main="location=0; scale=1; shape=4",
   xlab="sample data", ylab="probability")
lines(density(data), lwd=2)
x = seq(-20, 20, by=0.01)
y = dsn(x, xi=location, omega=scale, 
        alpha=shape)
lines(x, y, lwd=2, col="red")
```

---

## References

For more information on skewed normal distributions and the sn R package see [The Skew-Normal Probability Distribution](http://azzalini.stat.unipd.it/SN/) by Adelchi Azzalini.

The source code of this presentation can be found on [github](https://github.com/rubberbandman62/skewedDistributionsPitch/tree/gh-pages).

A Shiny App to demonstrate the effect of the three parameters $\xi$, $\omega$ and $\alpha$ can be found on [shinyapps.io](https://rubberbandman62.shinyapps.io/skewedDistributions/).

The source code of this Shiny App is also stored on [github](https://github.com/rubberbandman62/skewedDistributions).


