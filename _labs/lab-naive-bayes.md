---
title: "Lab: Evidence Combination"
---

This lab will use Naive Bayes.

Download [this workbook](https://github.com/brhu6775/business-analytics/blob/master/_labs/NaiveBayes-example-fill-in.xlsx?raw=true) (click the three ... in upper-right corner, “download). 
It contains historical data on whether online consumers will make a purchase on your website. For each consumer, you know whether they visited certain kinds of websites before visiting your site. The historical data is in rows 2 through 32.

Use this historical data to make a prediction for whether or not a new online consumer will make a purchase on your website. 
- To do this, first, compute each conditional probability, `p(x=1|C)`, in cells B18:F18, and cells B32:F32. Cells in rows 37 and 38 depend on these formulas being correct.

Then, calculate the probability that a new customer with the following Evidence vector will make a purchase on your site. 

`E = (1, 1, 0, 0, 1)   <-- plug these values into Row 36`


**Hint for the lifts:** To correctly interpret “lifts”, set the observed E vector to all 1’s. The lifts all answer the question, “how much more likely is observing this `c` if this `e` is observed?” Look at how, e.g., cell B37 is defined. It first checks if the corresponding evidence, B36, is actually observed. If it is not, this evidence is not considered for the calculation -- which is functionally obtained by setting the value equal to 1. Lifts are kind of calculated equivalently, in that to correctly calculate them, we assume that the `e` is actually observed. Review the slide deck and/or textbook for the lift formula.


#### Question 1:
----------
 For this new customer, what probability will naive bayes predict for `p(P|E)*p(E)` in cell H37?


#### Question 2:
----------
 If you wanted to make an actual prediction for `p(P|E)`, what would it be for this E vector in cell J39?

#### Question 3:
----------
Based on your training data, what is the lift of E_sports relative to being a purchaser (c=1) in cell B41?

#### Question 4:
----------
 What class membership prediction will a naive bayes algorithm trained on this historical data make for this new customer?

<ol class='list-style-upper-alpha'>
    <li>It's a tie</li>
    <li>Impossible to reliably say because of naive assumptions</li>
    <li>Not-Purchaser</li>
    <li>Purchaser</li>
</ol>

#### Question 5:
----------
Based on the historical data, what is the probability of a purchaser visiting a cooking website?
 
#### Question 6:
----------
Based on the historical data, what is the overall probability of visiting a health website?
 
#### Question 7:
---------- 
Which of the following most increases the likelihood of not being a purchaser?

<ol class='list-style-upper-alpha'>
    <li>Sports.com</li>
    <li>Finance.com</li>
    <li>gossip.com</li>
    <li>Health.com</li>
    <li>Cooking.com</li>
</ol>
 
#### Question 8:
----------
What is the overall probability of not being a purchaser?