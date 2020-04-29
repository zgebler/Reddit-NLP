# Reddit-NLP

## Overview and Current Status

- Investigation of how NLP can be applied to learning about Reddit communities (subreddits)

## Workflow

1. Pushshift API Interface - defines functions and downloads subreddit data from API
2. NLP and Classification - loads and transforms text data into model inputs for classification

## Problem Statement

- Can we predict which subreddit a post was submitted to?
- What distinguishing features about the subreddits can our model learn?

## Data

- The first two subreddits this model looks at are r/listentothis and r/hiphopheads
- Over a data range of 1/1/2020 - 3/25/2020, 31,674 posts were downloaded from r/hiphopheads and 30,528 were downloaded from r/listentothis
- Data was preprocessed, running in through a Tokenizer and Lemmatizer, removing generic stop words and punctuation.


## Modeling

- Pipelines were constructed to transform the corpus of words pulled from all of the titles into a sparse matrix that could be input into a Logtistic Regression Classification
- The first model uses a CountVectorizer transformer, the second uses a Tfidf Vectorizer

## Model Results

| Score | CountVectorizer + Logistic Regression | Tfidf Vectorizer + Logistic Regression |
|--- | :-:  | :-: |
Accuracy | 0.88366 | 0.88114    
Sensitivity | 0.84422 | 0.83955
Specificity | 0.92200- | 0.92158
Precision   | 0.91322 | 0.91234

- Both models performed significantly better than the baseline model, correctly predicting the subreddit of origin in more than 88.1% of the time.

## Interpretations

- Top 20 Distinguishing Words per Subreddit

| r/hiphopheads | r/listentothis |
| :-- | :-- |
fresh | indie
eminem | 2020
original | 2019
pop smoke | rock
lil | pop
album | electronic
rapper | folk
jay | 2018
drake | metal
kanye | punk
feat | alternative
hype | 2017
smoke | jazz
leak | band
ft | house
thread | liked youtube
kendrick | 2016
top | hop 2020
future | hop 2015
fresh video | 2014

From this list it becomes clear that there are posting guidelines or rules on the r/listentothis subreddit - posts must contain genre and year that the song was posted. More generally, we see that r/listentothis is more of a music recommender, as opposed to a discussion based forum like r/hiphopheads. 


## Further Questions
- How can NLP be applied to see how successful or engaging a post will be?
