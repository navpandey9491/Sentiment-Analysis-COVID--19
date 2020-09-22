# Sentiment-Analysis-COVID-19


## Problem Statement
To analyse tweets on the recent pandemic scenario and classify it into positive, negative or neutral on the basis of the sentiment it conveys.
To analyse the most positive and most negative words in the case study of three cities selected for sentiment analysis on the present COVID - 19 situation.


## Dataset 
To perform sentiment analysis, we need textual data containing expressions about the prevailing situation of COVID 19. Reddit API, Facebook API, Twitter API and scraping data from other public opinion polls were options to collect data.
Twitter is considered as a major psychological database and thus Twitter Sentiment Analysis also is used for monitoring and analyzing social phenomena, for predicting potentially dangerous situations and determining the general mood of the people across different cities.

While Tweepy is the most widely used library used to scrape tweets, using Tweepy we can only able to return up to 3,200 of a user’s most recent tweets. 
GetOldTweets3 is a library used here to bypass the twitterAPI limitation of only providing tweets upto 7 days of search. Also, GetOldTweets3 has a functionality of searching relevant tweets on the basis of place, language and geo-coordinates. Hence, this library was used for this project. We intended to not only perform sentiment analysis on the tweets but also derive data insights from the study of three major english speaking cities, such as, London, New York and Delhi. These cities were selected due to the availability of tweets in English language. Spain or Italy couldn’t be included in the study due to the language translation difficulty in the dataset.

The three variables I focused on are text_query, tweet place and count. text_query = 'COVID19',’CoronaVirus’ 
Also, it does not require any authentication like Tweepy does.

Thus, a dataset of each city was created using GetOldTweets3 with 5000 tweets each.

## Data Preprocessing

The first and foremost step of the machine learning Dropping repetitive rows of tweets

We scraped 15000 tweets but after dropping the duplicate rows, we are left with 12870. Having duplicate rows increases the accuracy and thus some classifiers give as high accuracy as 90%. 

### Dropping unnecessary data columns

We decide to keep only the relevant data columns, text and date & time. 

### Cleaning the tweets

The tweets consist of many irrelevant characters like hashtags and links. 
pipeline is to clean the tweets. Data contains multiple abnormalities like duplicate tweets, emoticons and hashtags. 
It is thus, very important to preprocess the data so that we can use it to derive meaningful insights. 
Dropping repetitive rows of tweets

We scraped 15000 tweets but after dropping the duplicate rows, we are left with 12870. Having duplicate rows increases the accuracy and thus some classifiers give as high accuracy as 90%. 

While we need to remove special characters, sometimes, the hashtags convey some meaningful information. For example, #facemasking can not be removed completely as it conveys an important sentiment in regard to the current situation of the Pandemic. Thus, we remove only the hashtag symbols from the tweets and the words are left as they were. ‘re’ module in Python was used for text cleaning. We replace all these symbols with a whitespace character using the re.sub() function. 
Also, username tags, URLs were replaced as seen in the code snippet attached below,

## Modeling

Ensemble Methods like Random Forest have performed fairly in the past and thus we chose it as the baseline for our model. Also, Random Forest is comparatively faster. The accuracy achieved using unigrams and tfidf vectors with Random Forest Classifier was 0.68429. We use the accuracy score to measure the performance of the model (precision score, recall and confusion matrix are also calculated). 

On researching more about the suitable method for the dataset we have in hand, we came across the fact that Random Forest Classification methods are intrinsically suitable in case of multiclass problems whereas SVM works better in case of two-class situations. 
For a text classification problem, Random Forest will yield the probability of that text belonging to one of the possible classes. SVM calculates distance to the boundary, which has to be converted to probability.

LinearSVC() has an accuracy of 0.83825 on our dataset, thus confirming the above proposition.
I have also tried other classifiers,
●	Naive Bayes models(MultinomialNB, BernoulliNB,)
●	Linear models (LogisticRegression, RidgeClassifier, PassiveAggressiveClassifier, Perceptron)
●	Ensemble models( RandomForest classifier, AdaBoostClassifier) 
●	SVM model(LinearSVC)

