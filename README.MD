# Project 3: Reddit Comparison Between Seinfeld and Curb Your Enthusiasm

## Problem Statement

I was tasked with comparing reddit posts in two subreddits; Seinfeld and Curb Your Enthusiasm. If I can classify TV shows just by using text that is talking about them then I could automate the process of sorting what show a quote is talking about.


## Executive Summary

I was taked with gathering data on two subreddits and chose to look at Seinfeld and Curb Your Enthusiasm (I will refer to this show as Curb going forward) and analyzing those posts.I gathered data on these two shows and used reddits API to bring in both posts and comments for these two shows. I created two datasets to analyze the data; one dataset included around 1000 Seinfeld posts and 1000 Curb posts and the other dataset included around 5000 Sienfeld posts and comments and around 5000 Curb posts and comments. So that I was not continuously pulling in data from reddit's API, I have one notebook titled "data_sets" that pulled in the data from reddit and another notebook titled "Submission" that has my data cleaning and modelling.

I started my cleaning process by getting rid of all columns that were not text or the name of the show. I then went on to binarize the column that contained the name of the show and got rid of all instances of websites from my text data. I also decided to get rid of all non-english alphabetical characters and the instances of the word "Episode" since these did not help in determining subreddits. I got rid of all stances of the words "removed" or "deleted" since that means that the posts were removed or deleted so I did not have all the information from these posts. Finally I decided to lemmatize my text so that I would not be analyzing different versions of the words.

I created models for both my dataset with just posts and my dataset with posts and comments. For all models I set my X to be the body of my text and my y to be what the subreddit was and conducted a train test split on my data. For my first model for the posts dataset I used a logistic regression used count vectorizer to break up by words, meaning each word was given the same weight. I left all parameters unchanged for my model and was able to obtain training scores of 99.5 percent and a testing score of 86.5 percent. I then I used Multinomial Naive Bayes model and vectorized used TFIDF which is unique because it gives increased weights to unique words and less weight to words that are used often. Using this model I was able to optain a training score of 98.6 percent a testing score of 89.5 percent. As you can see this new model was able to increase my testing score and decrease the overfitting problem. Lastly I used a Random Forest Classification model and TFIDF vectorizer to fit my data. I was able to obtain a training score of 99.8 percent and testing score of 88.3 percent.

When testing my dataset that included both posts and comments I used all the same models so that I could see if there was any significance of having the comments data in my model. All my models were significantly more overfit when I included the comments with the best testing score being at 81 percent. I found my best model to be the Niave bayes model. What I also found suprising was that while the Random Forest model worked well for the data that included just posts it performed the worst by a large margin for the data that included posts and comments.

## Pertinent Documents

There are two notebooks that contain information, one being "Submission" which contains all my data manipulation and analysis and the other being "data_sets" which contains all the code which brought my data from reddit. There are four csv documents that allowed me to bring data from my "data_set" notebook to my "submission" notebook. Those csv's are titled "curb_post_all", "seinfeld_post_all", "curb_comment", and "seinfeld_comment". Lastly the curb_seinfeld_presentation is the presentation that I presented to my client.

## Conclusion

Overall I believe that it was best for me to use just the posts to analyze what show a commenter was talking about because all my models with posts and comments were very overfit. I also came to the conclusion that my Naive Bayes model was the best model because it was able to most accurately predict my testing data and had the least overfitting.
