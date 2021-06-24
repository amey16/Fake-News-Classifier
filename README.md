# Fake-News-Classifier
Finding fake news using NLP,ML algorithms
# Introduction

In the following analysis, we will talk about how one can create an NLP to detect whether the news is real or fake.<br/> 
Nowadays, fake news has become a common trend.<br/>
Even trusted media houses are known to spread fake news and are losing their credibility.<br/>
This is how i came up with an idea why not create a fake news classifier

# Dataset
The dataset was collected from kaggle - [click here](https://www.kaggle.com/c/fake-news/data) <br/>
- train.csv: A full training dataset with the following attributes:
    - id: unique id for a news article
    - title: the title of a news article
    - author: author of the news article
    - text: the text of the article; could be incomplete
    - label: a label that marks the article as potentially unreliable
        - 1: unreliable
        - 0: reliable
- test.csv: A testing training dataset with all the same attributes at train.csv without the label.
- submit.csv: A sample submission that you can

# Architecture
![WhatsApp Image 2021-06-24 at 18 49 41](https://user-images.githubusercontent.com/51751926/123269870-046dba80-d51d-11eb-8e61-0cc117da37f7.jpeg)

# Vectorizers
Word Embeddings or Word vectorization is a methodology in NLP to map words or phrases from vocabulary to a corresponding vector of real numbers which used to find word predictions, word similarities/semantics. The process of converting words into numbers are called Vectorization.
<br/>
- Vectorizers used:
    - Count Vectorizer(Bag of words) :<br/> ![image](https://user-images.githubusercontent.com/51751926/123270616-b1483780-d51d-11eb-898c-94041850d414.png) 
    - TF-IDF Vectorizer - Ensures that semantic meaning is restored <br/> ![image](https://user-images.githubusercontent.com/51751926/123270784-d6d54100-d51d-11eb-84be-56bb6a285c46.png) 
    - Hashing Vectorizer - Applies a hashing function to term frequency counts(semantic meaning reserved) <br/> ![image](https://user-images.githubusercontent.com/51751926/123271478-80b4cd80-d51e-11eb-9de8-27175841965d.png)

# Algorithms
- Mutinomial NaiveBayes
    - The multinomial Naive Bayes classifier is suitable for classification with discrete features (e.g., word counts for text classification).
    - The multinomial distribution normally requires integer feature counts.
    - However, in practice, fractional counts such as tf-idf may also work. 
- PassiveAgressive Classifier
    - Passive-Aggressive algorithms are somewhat similar to a Perceptron model, in the sense that they do not require a learning rate.
    - However, they do include a regularization parameter.
    - Passive: If the prediction is correct, keep the model and do not make any changes. i.e., the data in the example is not enough to cause any changes in the model. 
    - Aggressive: If the prediction is incorrect, make changes to the model. i.e., some change to the model may correct it.

# Results
The results in the table below are the results after taking best alpha values using hyper-parameter tuning for Multinomial NaiveBayes <br/> 
Model used | vectorizor type | Accuracy
:---: | :---: | :---:
Multinomial NaiveBayes | Count vectorizer | 0.94279
Multinomial NaiveBayes | TF-IDF vectorizer | 0.94375
Multinomial NaiveBayes | Hashing vectorizer | 0.94087
Passive Agressive classifier	| Count vectorizer | 0.96755
Passive Agressive classifier	| TF-IDF vectorizer | 0.97981
Passive Agressive classifier	| Hashing vectorizer | 0.98293
<br/>
We see that although the MultiNomial NaiveBayes with bag of words model has a general accuracy of 94.3 %, which is good, but it does not really score well in view of number of false negative. 223 fake news are classified as true news with this model, which is not pleasing to see<br/>
Similarly using TF-IDF and hashing vectorizor almost same trends were noticed .So,trying a different model altogether<br/>
<br/>
We get much better results than with the MultinomialNB model(passive -agressive classifier + count vectorizor), both in terms of accuracy and in terms of false negative. Only 60 fake news were labeled as true news this time. similar trends with the Tf-IDF method.<br/>
The model with hashing vectorizor and Passive-Agressive classifier performed the best with only 30 fake news labeled as true news
