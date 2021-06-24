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
