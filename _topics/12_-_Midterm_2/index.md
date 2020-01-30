---
title: 12 - Midterm 2
---

# Analytics Topics for Second Exam

## Generally
* Do not generally need to memorize formulas unless I say so below.
* Do not need to be prepared to use Alteryx, DataRobot, or any tool besides pen-and-paper for simple math calculations
* Do need to conceptually understand the principles of business analytics that we have discussed so far
* Do not need to understand principles in the book that we have not discussed in class...
   * But the book will be monumentally helpful towards your conceptual understanding of what we have discussed.

##Supplemental Book Chapters
* 9,6,12,10

## Overarching Concepts from first half of class
* CRISP-DM and each of its phases
* Unsupervised vs supervised learning
* The strictly conceptual need for and use of the following for predictive analytics:
   * ETL
   * Transformations / feature engineering 
      * Joining, summarising

## General concepts
* Classification vs continuous prediction models; the different classification algorithms we have covered so far
* Understand how to interpret probability syntax when expressed as e.g. p(A|B)
   * You should be able to interpret this in the context of a confusion matrix too, although I already tested you on that

## Lecture: Prediction via Evidence Combination
* Calculation of combined probabilities under assumptions of independence and dependence
* Understanding what is meant by p(Y|X) where Y is some class, and X is a feature vector -- that predicting such is the ultimate goal of classification algorithms
* Understand why p(X|Y) * p(Y) is easier to calculate than is p(Y|X) * p(X)
   * p(Y|x) = p(measles | red spots)
   * p(x|Y) = p(red spots | measles)
* Understand conceptually why naive bayes is “naive”
* Understand advantages and disadvantages of naive bayes
* Evidence lift, including how to calculate, how to interpret, and why it is doubly naive.

## Lecture: Similarity and Nearest Neighbors
* Similarity
   * Business use-cases for similarity -- e.g., “similar” products, movies, books, customers, law cases, health cases
   * Distance calculations:
      * Euclidian distance
      * manhattan distance
      * jaccard distance vs simple matching coefficient
      * (Later, for text mining, cosine distance, conceptually)
* Nearest Neighbors
   * Uses for predictive modeling when combined with similarity
   * How to give “closer” neighbors more “influence”
   * Impact of choice of k, number of neighbors -- conceptually, k=1 neighbor vs k=n neighbors
   * Advantages and disadvantages of nearest neighbor models

## Lecture: Unsupervised Data Mining and Clustering
* Hierarchical clustering
   * Concept of a link function
   * Use of a “threshold”
   * Interpretation of a dendogram
* Centroid-based clustering
   * Difference from hierarchical
   * Iteration process of centroid placement
* “Understanding” the results of clustering; How to “label” -- the two approaches, (1) average dimension values, and (2) supervised learning

## Lecture: Text Mining
* Why text is important, why it is difficult
* Vocabulary: document, corpus, tokens, terms 
* Converting text into feature-vector form, different approaches for
   * Bag of words, binary
   * Bag of words, term frequency
   * Preparing data: stop-word removal, stemming, case-normalization
   * Bag of words, inverse document frequency (IDF) and TFIDF
* Understand how a search engine might use text mining feature-vector representation to rank search results
* Cosine-distance, but not memorize the formula -- just how it is used for text, and how it uses feature-vector
   * I learned how this worked today, it’s a cool hack. Answers the age-old question of all high-school students of “why do I need to learn trigonometry if I am not going to be a civil engineer or a bird watcher?” Well, look at this: https://www.mathsisfun.com/algebra/vectors-dot-product.html This describes the “dot product” of two vectors. They say that it is equivalent to multiplying the length of two vectors by the cosine of the angle between them. Recall that cosine values range between -1 and 1. We like that property of cosine because we are looking for a “similarity” score between two text documents. So if you do a cool hack, you can divide the dot product of two vectors by the product of their lengths, and you get... the cosine of the angle between them :shrug:. That is a cosine similarity, so to switch it to a cosine distance, subtract it from 1. Voila, did you know that, now you know. It’s cool for things like text mining when using TF-IDF or other values that are non-integer so you can’t do a simple jaccard distance or simple matching coefficient. Sure, you could still do a euclidean or manhattan distance between two text feature-vectors, but for some reason still unknown to me, cosine distance is preferred for text comparison over those other two approaches.

   So go back and tell your high-school self to shut up and learn trig “you’ll thank me one day.”