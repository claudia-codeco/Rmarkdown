A very simple R markdown document
========================================================

Script structure
----------------

- Creating data
- Graphs
- Hipothesis test
- Modeling

Creating some *data*:
---------------------


```r
r1 <- 10 + rnorm(100) * 10
r2 <- 4.5 + r1 + rnorm(100) * 3
summary(r1)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -19.30    3.16    9.57   10.20   18.20   33.00
```

```r
summary(r2)
```

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##  -15.70    8.13   14.40   14.80   23.10   38.10
```





The mean of r1 is 10.241 r2 is 14.752.

Graphs
------


```r
par(mfrow = c(2, 1))
hist(r1, col = 2)
hist(r2, col = 3)
```

![plot of chunk graficos1](figure/graficos1.png) 


A scatterplot r1xr2
(using echo = False)

![plot of chunk graficos2](figure/graficos2.png) 



Hypothesis test
---------------

```{ttest r}
test <- t.test(r1,r2)
```

Regression Model
----------------


```r
reg <- lm(r2 ~ r1)
summary(reg)
```

```
## 
## Call:
## lm(formula = r2 ~ r1)
## 
## Residuals:
##    Min     1Q Median     3Q    Max 
## -5.602 -2.112 -0.665  1.727 10.516 
## 
## Coefficients:
##             Estimate Std. Error t value Pr(>|t|)    
## (Intercept)   4.7652     0.4112    11.6   <2e-16 ***
## r1            0.9752     0.0278    35.0   <2e-16 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.96 on 98 degrees of freedom
## Multiple R-squared:  0.926,	Adjusted R-squared:  0.925 
## F-statistic: 1.23e+03 on 1 and 98 DF,  p-value: <2e-16
```


The fitted curve is:


```r
plot(r1, r2)
abline(reg)
```

![plot of chunk egplot r](figure/egplot_r.png) 






