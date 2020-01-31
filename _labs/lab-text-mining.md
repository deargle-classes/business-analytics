---
title: "Lab: Text Mining"
---

This lab uses select data from https://www.kaggle.com/c/random-acts-of-pizza, 
 (Links to an external site.)
which is a collection of posts from https://www.reddit.com/r/Random_Acts_Of_Pizza/
 (Links to an external site.)
 , where the idea is that people can beg for someone to send them pizza. The data has flags indicating whether or not they received pizza.

I pulled out the titles of a few of the posts that did receive pizza. You will do some text analytics type stuff with these titles.




For the first set of questions, use [this excel spreadsheet](https://canvas.colorado.edu/courses/21394/files/2446645/download?wrap=1) In it, for each of the indicated tokens in each of the provided documents, calculate the TFs, as well as the IDF, and finally the TFIDF using the indicated TF. You can do the calculations in Alteryx if you really feel like it, but it's easy enough in Excel.

Hint: One way to check if a word is present in a document in Excel is like this:
* use the SEARCH function. If the string is found, it returns a numerical position of where the string was found. If the string is not found, it returns a... not number. An error of some sort.
* wrap the SEARCH function in a ISNUMBER function. This converts the output of SEARCH to a binary TRUE/FALSE
* use an IF function to check the output of the ISNUMBER function. IF true, then 1, else 0. Tada, you have a binary TF representation.

Here is a way to count the number of words in a string in excel: https://exceljet.net/formula/count-total-words-in-a-cell
 (Links to an external site.)
. This approach works by counting the total number of characters in a string, and subtracting from that the total number of characters in a string if spaces are removed, and adding 1. You should `trim()` all string references so that any trailing white-spaces are removed or this approach will report inflated word counts.

Do not worry about stop word removal or stemming for these questions. In fact, do not remove anything from anything.




**Question 1:**
What is the value in cell D17 -- the binary length-normalized TF of "girl" in text 3344? To four decimal places.
 

**Question 2:**
What is the value in cell E23 -- the IDF of "broke"? To four decimal places.
 
**Question 3:**
What is the value of C31 -- the TFIDF of "college" in text id 3344? To four decimal places.
 

For the following questions, use [this workbook](https://canvas.colorado.edu/courses/21394/files/2225101/download?download_frd=1).

The goal for these questions is Information Retrieval. You are given the title of a post, and you are to calculate the cosine similarity between that title and all other titles in the given corpus. The workbook has more tips on how to do that.
For each title, a feature-vector is provided for you. Use the entire provided feature vector to calculate your similarity scores.
 
**Question 4:**
What is the highest similarity score?
 
**Question 5:**
What is the id of the text that is most similar to the query text?
 
**Question 6:**
What is the id of the text that is most dissimilar to the query text?