# Project 3: Web APIs and NLP

## Problem Statement

Reddit is a huge collection of online discussions and forums of varying topics and subjects, that forms into communities over time. However, the vast number of subreddits can be overwhelming for new users, especially when there can be multiple subreddits that have similar discussion topics. 

The objective of this project is to produce a model which can accurately classify which subreddit a specific post belongs to, from the two subreddits- r/Netflix and r/AmazonPrimeVideo. Given that both of these involve discussions regarding the respective video streaming platforms, it would be a good test to see if the model can accurately classify posts from similar subreddits.

The results can be utilised by users who are unsure which subreddit their new post would be the most appropriate for, so that they can attract more engagement and minimise post removal from the subreddit moderators.


## Data Extraction & Cleaning

The Pushshift API was used to pull submissions/posts from the two subreddits that would later be used for training the model and predicting the outcome. The number of posts pulled was 1000 for each subreddit and selected based on certain cutoff UTC epoch values.

Many posts consist of punctuations, symbols, numbers, and some even have their content removed. These were discarded with the use of the RegEx Tokenizer, while words that have past or future tense were reverted back to its root word through lemmatization. The words are then join back into a string and used for further exploration and analysis.


## EDA

Within the 20 most frequent words, the most that appeared the most are video streaming terms, such as 'netflix', 'show', 'movie', 'season', etc.; while simimlarly, the most occuring words within r/AmazonPrimeVideo are relevant to video streaming terms as well, outside of the common 'amazon' and 'prime', words like 'video', 'movie', 'watch', etc. appears a lot.

To take the analysis to a deeper level, the ngram_range for the vectorizers was increased to (2, 2) to reflect bigrams, which are two adjacent elements within a string of tokens in sequence.

By changing the vectorizer to only identify bigrams, it can be observed that there are multiple names of shows that occur frequently within r/Netflix, and they happen to be original shows produced by Netflix. This trend is observed as most of the submissions pulled from the subreddit is relatively recent, and most of these shows have only recently been released.

On the other hand, the plots from r/AmazonPrimeVideo does not display as many original show names, and the most frequently seen bigrams are 'prime video' and 'amazon prime' when the dataset ran through both the CountVectorizer and TFIDFVectorizer. The only notable bigram that could be relevant to a show would be 'boy season', which is most likely reflecting the show 'The Boys'.


## Modeling & Evaluation

The baseline accuracy to predict whether a post is within r/Netflix is approximately 0.51.

By splitting the dataset into training and testing sets, it can then be fitted to the classification models that would potentially predict the outcome accurately. A pipeline with the vectorizers (CountVectorizer, TFIDFVectorizer) and models (Random Forest, Multinomial Naive Bayes). GridSearch was used to determine the best vectorizer, model and hyperparameters to get the best fit model with a good bias-variance tradeoff score. Based on that, the CountVectorizer with the ngram_range of (1,2) and english stop words removed, used with the Multinomial Naive Bayes model on a smoothing parameter (alpha) of 4.0.

Training score: 0.8321690461225344
Test score: 0.82574568288854

- The model was able to correctly predict 82.6% of the observations.
- Misclassification rate: 17.4%
- Among posts that the model predicted to be in r/Netflix, 83.0% of them were correctly classified.
- Among posts that are in r/Netflix, the model has 83.0% of them correctly classified.
- Among posts that are in r/AmazonPrimeVideo, the model has 82.0% of them classified correctly.


## Limitations

Based on the observations above, we can see that the misclassified posts have very generalised uses of words and terms, which could throw off the model as these posts do not have clear signs that they fall within either subreddits. There are also a post with the word 'netflix' but was misclassified within r/AmazonPrimeVideo. 

Some identifiable outliers within this dataset would be the shows that are part of both streaming platforms and are mentioned in both subreddits, or a post within r/AmazonPrimeVideo that compares between the various video streaming services (Netflix, AmazonPrimeVideo, Hulu, Disney+). This could cause a slight miscalculation by the model if the word 'netflix' is given enough importance that would cause it to be predicted to fall within r/Netflix. However, given the size of the pulled dataset and low likelihood of a similar scenario occurring, it can be overlooked for this project.


## Conclusion & Recommendation

The Multinomial Naive Bayes classifier performed well with a test accuracy score of 82.6%. This is within expectations because the topics of our two chosen subreddits are relatively similar. As such, a Subreddit Classifier web application can be developed, where users can submit their draft post in the application to determine which of the two subreddits would be the most suitable for the post for a potential use case.

Scope for future improvements:
- Optimize stop words and explore strategies for stemming and lemmatization
- Run the model through more historical and live updated data, since the subreddits are constanly being updated with new submissions
- Ability for model to classify more than two subreddits
