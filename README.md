# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 3: Web APIs & NLP


### Problem Statement 

I have been hired by a new company that is trying to develop a tool to predict customers gender based on comments/reviews in order to develop their marketing intelligence. I chose to study two gender based subreddits(AskMen/AskWomen) and to build a model to see if there is a recognizable pattern and the actual ability to predict the gender of an author online.



### Data Collection and API

For this project I didn't have access to structured data and I had to pull actual posts from two subreddits:
https://www.reddit.com/r/AskMen/ and https://www.reddit.com/r/AskWomen/

I used the pushshift API to scrape this data. The interesting part of it was to write a function that used a timer
to not overload the reddit server and not appear as a threat. In addition to the timer, I had to go back in time each 100 posts
for the 4000 posts collected. I learned about the UTC timecode or coordinated universal time usually used by meteorologist. 


### Data Cleaning and EDA

Since it was all unstructured data, I had some challenges normalizing the data for further analysis and modeling.
First I had to get rid of a large number of columns/features that were not relevant to my project.
Aside from the habitual null values, I had to also remove any duplicated post from the dataframe.
Natural language processing requires the removal of numbers; which are not words. 
Another step I had to take was to remove any post in a foreign language because some of the posts in the dataframe were in arabic.
Lastly, I use the count vectorizer to analyze the frequency of each words from posts of both subreddit.


### Preprocessing

In order to build a model with this data I had to I had to TDIF vectorize, stem and use stop words.
The TDif vectorization allowed me to penalize the most common words by attributing a weight to each words.
The most common words receive a low figure. The stem process allowed me to delete any suffixes like verb conjugation (swimmer/swimming). During the EDA process I realized that some of the most common words wouldn't add any relevancy
like "did". The stop words remove those unnecessary words.


### Modeling

For this project, I focused on two main classification models. The first one was a logistic regression and the second one 
was a random forest classification model. Both model performed badly and had the same approximate accuracy score of 69%.
Out of the two, the random forest model performed slightly. better.


### Conclusion

The best model between logistic regression and random forest was the later, the random forest model. I was only able to accurately predict the classification of a post 69% of the time.

To possibly improve this score, I'd probably need to stratify the classes to ensure that the minority class is accurately represented in our model. I'd also probably need to do a combination of oversampling/undersampling of the minority or majority class.

In less technical terms, while I had a good feeling about finding a pattern in posts from the AskWomen subreddit and the AskWomen subreddit, I couldn't find a clear one. The most common words are pretty similar in both subreddit with generic words like women/men, like, know, feel.

The context is important here because this is mainly a forum where people ask questions: "Do you men fee like/Do you women feel like...?" Consequently, these posts don't reflect the way customers would comment on a product/service.

Another approach to improve this model would be to perform a sentiment analysis to see the differences in both subreddits and get more representative data, like actual reviews.

Overall, I pretty much consider this test as a failure and I hope I won't get fired !



