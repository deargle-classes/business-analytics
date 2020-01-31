---
title: "Lab: Model Performance and Expected Value Framework"
---

## Question 1

Read [https://www.schneier.com/blog/archives/2006/03/data_mining_for.html](https://www.schneier.com/blog/archives/2006/03/data_mining_for.html)

You are a credit card company. "There are 900 million credit cards in circulation in the United States. 
According to the FTC September 2003 Identity Theft Survey Report, about 1% (10 million) cards are stolen and fraudulently used each year."
Assume that you have a model that correctly classifies 90 out of every 100 actual positives. But, it also incorrectly flags as positives 
10 out of every 100 negatives. Create a confusion matrix, in millions (e.g., if the answer were "900 million", type "900"). For the matrix, use a total N of 900.


||p|n|
|Y|||
|N|||

```
p = actual yes
n = actual no
Y = predicted yes
N = predicted no
```


## Question 2
Using the confusion matrix above and the description in the text, match the following values to the correct metric.

```
TPR (aka `recall` aka `sensitivity`) 
           [ Choose ]             0.1112             0.20             0.80             0.10             0.90             0.5             .0918             0.1666         
FPR 
           [ Choose ]             0.1112             0.20             0.80             0.10             0.90             0.5             .0918             0.1666         
PPV (aka `precision`) 
           [ Choose ]             0.1112             0.20             0.80             0.10             0.90             0.5             .0918             0.1666         
F1-score 
           [ Choose ]             0.1112             0.20             0.80             0.10             0.90             0.5             .0918             0.1666         
```

## Question 3
You are a judge. You would like to use a model to predict whether someone is guilty or not. You have the following cost-benefit  matrix:

``` 
b(Y,p) = 100
b(Y,n) = -150
b(N,p) = 0
b(N,n) = 0
```
 
That is to say, society "gains 100" if a guilty person goes to jail, "loses 150" if an innocent person goes to jail "loses nothing" if a guilty person walks free, and "loses nothing" in an innocent person walks free. (Note that in reality, society does lose something if a guilty person walks free, but we're making a simplifying assumption for this thought exercise).
 
Your model makes a prediction for whether or not someone is guilty. At what minimum probability should you declare someone "guilty"?

## Question 4
Now make the assumption that there actually is a cost to a guilty person walking free.
 
```
b(Y,p) = 100
b(Y,n) = -150
b(N,p) = -100
b(N,n) = 0
```
 
Where:
```
Y = guilty verdict
N = innocent verdict
p = actually guilty
n = actually innocent
```
 
Before, we only had to consider the Expected Value for if we made a "guilty" prediction. Now, we need to separately model the expected value for if we make a "guilty" prediction and for when we make a "innocent" prediction.
 
Like this:
 
```
EV with "guilty" prediction = p(p) * b(Y, p)  + p(n) * b(Y, n)
EV with "not guilty" prediction = p(p) * b(N, p) + p(n) * b(N, n)
```
 
You should make a guilty verdict when "EV with guilty prediction" > "EV with not guilty prediction".
 
At what probability of actually-guilty should you make a guilty verdict? I.e., `p_guilty > _____`?