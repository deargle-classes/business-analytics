---
title: "Lab: Discriminant Functions"
---

## R-squared

This question requires some on-your-own reading. Linear regression models are often evaluated using metrics such as r-squared. 
Read about r-squared hereLinks to an external site.: Coefficient of determination. For the following questions, use this formula for 
R-squared. LaTeX: Rsquared\:=\:1\:-\frac{\:SSres}{SStot}R s q u a r e d = 1 − S S r e s S S t o tRsquared=1−SSresSStot


The basic idea behind sums of squares is that you calculate the distance (calculate the difference) between some point and another point, 
e.g., difference between mean of actual y's and actual y's, one point-pair at a time. Then you square that difference. Then you "sum" all 
of those "squares". SS_res stands for SS_residuals, and residuals are the differences between your predicted values and the actual values. 
SS_tot is the difference between the actual values and the average of all actual values. By dividing SS_res by SS_tot, you get an idea 
about how far the actual points are away from your prediction line, compared to how far away each point is to the average of all actual 
points (a flat horizontal line). It tells you how "good", or how predictive, your model is. The lower the SS_res, the higher the resultant r-squared.

Assume that you have a model that makes the predictions found in the file [cars.csv](https://raw.githubusercontent.com/deargle/deargle.github.io/master/class/data/cars.csv). 
Use whatever tool you like to answer the following questions.


**Question 1:** What is SSres for the data above?

**Question 2:** What is SS_tot for the data above?

**Question 3:** What s R-squared for the data above?


## Logistic Regresion

You induce a logistic regression model to predict whether someone will default on a loan. 

The main effect of `dti`, the main effect of `grade`, and the interaction of `dti` and `grade` 
were modeled to predict the likelihood of defaulting. An "interaction" is just like a regular feature, 
except that the interaction "weight" is assigned to the multiplication of two features. In the below case, 
it in effect gives a differential slope for `dti` to individuals in different grades. The "main effect" of 
`dti` is specified, as is the `main effect` for the different grades, along with an "interaction effect" for `dti:grade`.

If you are curious: In an R formula, `y ~ dti * grade` expands to `y ~ dti + grade + dti:grade`, 
where a colon specifies an interaction.

The model output provides the following summary:

```r
Call:
glm(formula = loan_status ~ dti * grade, family = binomial, data = mine2)


Deviance Residuals:
        Min           1Q   Median           3Q          Max 
-1.1609  -0.6066  -0.4712  -0.3473   2.6631 


Coefficients:
                  Estimate Std. Error z value Pr(>|z|)        
(Intercept)      -3.516919   0.229746 -15.308  < 2e-16 ***
dti               0.048308   0.012344   3.914 9.09e-05 ***
gradeB            0.839814   0.268586   3.127  0.00177 **
gradeC            1.501448   0.267276   5.618 1.94e-08 ***
gradeD            2.011791   0.281292   7.152 8.55e-13 ***
gradeE            1.866544   0.360583   5.176 2.26e-07 ***
gradeF            2.636531   0.654769   4.027 5.66e-05 ***
gradeG          -33.269100 723.723955  -0.046  0.96333        
dti:gradeB       -0.015668   0.014276  -1.097  0.27243        
dti:gradeC       -0.022040   0.014108  -1.562  0.11824        
dti:gradeD       -0.032202   0.014747  -2.184  0.02899 * 
dti:gradeE       -0.006724   0.018508  -0.363  0.71637        
dti:gradeF       -0.043739   0.031532  -1.387  0.16541        
dti:gradeG        1.837573  32.760837   0.056  0.95527        
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

(Dispersion parameter for binomial family taken to be 1)


Null deviance: 8070.2  on 9999  degrees of freedom
Residual deviance: 7647.0  on 9986  degrees of freedom
AIC: 7675


Number of Fisher Scoring iterations: 13
```

_dti_ is
A ratio calculated using the borrower’s total monthly debt
payments on the total debt obligations, excluding mortgage
and the requested LC loan, divided by the borrower’s selfreported
monthly income.
 
_loan_status_ is
The target values are therefore: 0 = Fully Paid and 1 =
Charged off (default).
 
_grade_ is lending-club-assigned loan grade. "A" is good, "G" is bad, etc.




**Question 4:** Refer to the model output above. What value would this model directly predict (y) for someone with a dti of .94 and a grade of D?
*[ ] y= 2.057
*[ ] y= 2.027
*[ ] y= -1.490
*[ ] y= 2.028


**Question 5:** Refer to the model output above.
What value would this model predict for someone with a dti of .3 and a grade of A?
*[ ] y= -3.502
*[ ] y= 0.014
*[ ] y= 0.048
*[ ] y= -3.469


**Question 6:** Assume that the model above make a direct prediction of y = .2. What would this be in terms of probability?
*[ ] p = .200
*[ ] p = .4
*[ ] p = .550
*[ ] p = .450