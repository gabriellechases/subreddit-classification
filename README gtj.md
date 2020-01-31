# Project 3 - Web APIs & Classification

## Table of Contents

- Problem Statement
- Data Collection
- Data Cleaning and EDA
- Preprocessing and Modeling
- Evaluation and Conceptual Understanding 
- Conclusion and Recommendations 

Identify the Problem Statement:**

The goal of this project is to use API to extract posts from two different subreddits and analyze the text from each. Natural Language Processing (NLP) - CountVectorizer and TF-IDF Vectorizer - and various classification methods will be used in order to determine if my models can predict the subreddit source a cerratin post is taken from. This is a binary classification problem. Logistic regression models (considered KNN and SVM), decision trees, and naive bayes (required) will also be applied in this project to test if the baseline score can maybe be outperformed. 

The question is whether machine learning can determine the approval ratings using NLP, by classifying if a given reddit post originates from r/Republican or r/Democratic. (source: https://observer.com/2016/02/these-9-reddit-communities-will-help-you-decipher-and-discuss-the-presidential-race/)

My targeted users are data scientists who are in the employment of potential presidential candidates running for in the 2020 campaign . 

Executive Summary:**

As part of data wrangling and acquisition, information is requested from an API, scraped. 

To convert into standard text data, ie titles and comments, NLP is utilised that can allow analysis and modeling to be conducted. 

Given the classification problem, classification modeling is done as a means of assessment and classification preprocessing. 

Data Collection:**

Data gathering, through an API, shows r/Democrats with 1834 posts and r/Republican with 1856 posts of various stuff for instance policy, impeachment and candidates. A function in my .ipynb notebook to pull each subreddit. A CSV file is created where the 2 subreddits are merged together. 

Data Cleaning and EDA:**

Firstly, there are some missing data (null values), duplicate posts, whitepaces and HTML formatting that needs to be rectified. A target variable is created - Republican as 1 and Democrat as 0 - for mapping purposes. 

Combined selftexts and titles to just create a title column. (Many posts had no selftexts, drop selftexts column.) A forloop is crucial when the subreddits are being scrapped while I run the API multiple times API caps the data at 1000 posts for each subreddit.

Another function created to convert raw text to a string (of words). BeautifulSoup will be used to remove any HTML. Any Upper texts will be converted to lowercase using the .lower(). Function will be used to combine any overlaps of two sets of words from the two subreddits so as to create stopwords for the modeling process. The stop_words('english) will be used to converted stopwords to a set and remove any stopwords followed by using WordNetLemmatizer(). CountVectorizer will also be applied. After data cleaning, a new clean version will be saved as a csv.

Preprocessing and Modeling:**

- Collected 1834 posts from r/Democrat
- Collected 1856 posts from r/Republican
- The actual data consistsed of titles, selftext, and the subreddit
- I used a function found in my python file to pull each subreddit
- Data consisted of policy, issues, and candidates
- Merged each subreddit into one csv.

First and foremost, the train data has the columns that will be used for the generation and refinement of the models. The test data will have the same columns, except the target that I set to predict in my Regression model. A regression model will be generate based on the train data, where I will validated it through train-test-split, cross-validation/ gridsearch for hyperparameters, analysis to see if there are any relationship (correlation) between predictive variables,  feature transformation (preprocessing)

![Screenshot 2020-01-31 at 11.24.54](/Users/gabriellechases/Documents/Screenshot 2020-01-31 at 11.24.54.png)

![Screenshot 2020-01-31 at 11.25.02](/Users/gabriellechases/Documents/Screenshot 2020-01-31 at 11.25.02.png)

Conclusion and Recommendation:**

It is obvious that my models were overfit. Adding more features such as comments, upvotes, scores could decrease overfitting. The model chosen is the Naive Bayes as it has the highest accuracy score.

Running my models without stopwords scored lower.

The most dominating feature in my model was 'Trump'. Incorporating sentiment analysis could be helpful to weight which words were more or least important.

In the future, I recommend running my model on different subreddits to see what scores it could yield. For example, adding another subreddit such as r/politics would add more signal to my model.