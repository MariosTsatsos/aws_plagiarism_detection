# AWS Plagiarism Detection
A Plagiarism Detector built using sklearn binary classifiers. The following three notebooks and supporting scripts (helpers.py and train.py) classify a given answer text as plagiarised or not by comparing it against a data base of texts. The data come from University of Sheffield's work on "Plagiarised Answers" https://ir.shef.ac.uk/cloughie/resources/plagiarism_corpus.html 

We classify a text as plagiarised (which includes "near copy", "light revision" and "heavy revision") and non-plagiarised.


This project breaks down to three main notebooks:

**Notebook 1: Data Exploration**
* Load in the corpus of plagiarism text data.
* Explore the existing data features and the data distribution.

**Notebook 2: Feature Engineering**

* Clean and pre-process the text data.
* Define features for comparing the similarity of an answer text and a source text, and extract similarity features.
* Select optimal features, by analyzing the correlations between different features.
* Create train/test `.csv` files that hold the relevant features and class labels for train/test data points.

**Notebook 3: Train and Deploy Your Model in SageMaker**

* Upload train/test feature data to S3.
* Define a binary classification model and put the details in a separate training script.
* Train the model and deploy it using SageMaker.
* Evaluate the deployed classifier.



To define similarity between any two texts I use i) containment value (similar to Jaccard similarity extended over n-grams) and ii) cosine similarity for n-grams n=1 to n=12 (or whatever the user deems important). The least correlated (four) features are selected in order to train a model. k-Nearest neighbours is chosen as it provides both high accuracy and metrics and also is conceptually simple, resource sparing and intuitive.


See also the paper "Developing a corpus of plagiarised short answers" by Paul Clough and Mark Stevenson, published in Lang Resources & Evaluation (2011). 

Part of Udacity 'Machine Learning Engineer' nanodegree.

