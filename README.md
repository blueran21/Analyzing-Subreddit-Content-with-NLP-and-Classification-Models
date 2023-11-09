#  Data Science vs. Software Engineering: Analyzing Subreddit Content with NLP and Classification Models


## Content
- [Problem Statement](#Problem-Statement)
- [Datasets](#Datasets-and-Data-Cleaning)
- [NLP](#NLP)
- [Model Building](#Model-Building)
- [Conclusions](#Conclusions)


## Problem Statement
In today's rapidly evolving technological landscape, data science and software engineering are two highly interconnected fields that have gained significant traction and attention. While both fields share some common ground and often overlap in certain aspects, they also have distinct differences in their objectives, methodologies, and skill sets. Gaining a deeper understanding of these differences can be crucial for individuals and organizations in making informed decisions about their career paths, education, and project development.

The goal of this project is to develop a natural language processing (NLP) and classification model that can accurately predict whether a given post belongs to the 'datascience' or 'softwareengineering' subreddit. By analyzing the textual content of posts from these two subreddits, the model will be able to identify distinguishing patterns and features that are characteristic of each subreddit's topic. This classification task will be approached using various machine learning algorithms, such as Naive Bayes, Logistic Regression, and Random Forest, to compare their performance in predicting the correct subreddit for a given post.


## Datasets and Data Cleaning
I retrieved posts from the 'datascience' and 'SoftwareEngineering' subreddits using the Pushshift API. The imported submissions, which encompass selftext and titles, were collected up until Aprile 19, 2023, at 7:19:19 PM. Each subreddit contains 5997 submissions. I combined the datasets from the two subreddits and treated each title or selftext as an individual document to increase the total number of observations. After removing missing and duplicated entries, as well as rows containing "\[removed\]" and "\[deleted\]" text, I was left with 6682 documents for "SoftwareEngineering" and 7993 for "datascience".
|Feature|Type|Dataset|Description|
|---|---|---|---|
|**selftext**|object|datascience|The self text of the post|
|**title**|object|datascience|The title of the post|
|**subreddit**|object|datascience|The subreddit name|
|**selftext**|object|SoftwareEngineering|The self text of the post|
|**title**|object|SoftwareEngineering|The title of the post|
|**subreddit**|object|SoftwareEngineering|The subreddit name|
|**selftext**|object|SoftwareEngineering|The self text of the post|
|**title**|object|SoftwareEngineering|The title of the post|
|**text**|object|data_cleaned|The text of either selftext or title|
|**subreddit**|object|data_cleaned|The subreddit name|
|**length**|object|data_cleaned|The character length of each text|
|**word_count**|object|data_cleaned|The word length of each text|


## NLP
I constructed stopwords using nltk and lemmatized the text. Subsequently, I employed regular expressions to remove punctuation and emojis present. For text vectorization, I utilized two distinct methods: CountVectorizer and TF-IDF Vectorizer. These preprocessing steps ensured the dataset was optimally prepared for the development of a classification model capable of effectively distinguishing between the two subreddits.


## Model Building
I experimented with three classification models: Logistic Regression, Multiple Naive Bayes and Random Forest. I employed the Pipeline and GridSearchCV tools from the sklearn library to optimize hyperparameters, including different vectorization methods, n-gram ranges, minimum and maximum word frequencies, maximum feature selection, and other relevant parameters. To evaluate the performance of each model, I used cross-validation to obtain accuracy scores as the metric. Furthermore, I implemented two ensemble methods: weighted averaging and Stacking.
## Conclusions
In conclusion, I utilized three classification models for the NLP task of differentiating between the 'datascience' and 'SoftwareEngineering' subreddits: Logistic Regression, Multinomial Naive Bayes, and Random Forest. The test accuracies achieved by these models were 0.843, 0.834, and 0.822, respectively. To further improve the performance, I employed two ensemble approaches, combining the predictions of the three classifiers. This resulted in an increased accuracy of 0.846 and 0.847, demonstrating the effectiveness of leveraging multiple models to enhance classification performance in NLP tasks.
