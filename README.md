# Tucker Carlson Bot Predictor - Phase 4 Project
This project is to predict how closely a given Twitter user aligns with Tucker Carlson's viewpoints.


## Navigating this Repo

This repo is broken into three main notebooks:

1. Webscraping notebook
2. Preprocessing notebook
3. Model analysis and prediction notebook

## Methods

We scraped the transcripts of over 900 Tucker Carlson Tonight episodes from Fox News using a combination of the Selenium Chrome WebDriver and BeautifulSoup. To collect Twitter data we interfaced with the Twitter API using the Tweepy library for python, first generating a random sample of roughly 3,600 users that have discussed politics, and then pulling the tweet history from these users.

We trained the model on transcripts from Tucker Carlson Tonight with the goal of identifying 10 unique topics, and then manually labeled these topics according to the top 10 words in each topic. The topics were as follows:

1: American Politics, 2: War in Ukraine, 3: Covid-19 in America, 4: School, 5: Biden Administration, 
6: War in Afghanistan, 7: Trump, 8: Abortion, 9: Kyle Rittenhouse Shooting, 10: Covid-19 World Outbreak

Next, we took the topic model and applied it to the tweets of every user, creating a distribution of how frequently each user discusses the various topics. We did the same process for Tucker Carlson's dataset.

We then took the topic distribution vector of each Twitter user and Tucker Carlson to calculate the cosine vector similarity between the two. Twitter users that have a cosine similarity above 0.5 were classified as having similar interests as Tucker Carlson, and those below were classified as disagreeing with Tucker Carlson.

## Conclusion

We found the classification method to work sufficiently well as a "proof-of-concept" but more work needs to be done to make the model a practically effective tool. Specifically, manually labeling a sufficient amount of data would allow us to leverage more powerful NLP tools such as BERT fine-tuning to understand the stances of each Twitter user.

