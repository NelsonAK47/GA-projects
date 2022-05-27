
# Project 3 - Web APIs & NLP Analysis on Dota 2 vs League of Legends Subreddits

## Background
Reddit is the most popular discussion-based social media in the world and ranked as the 8th most popular website in the world [(*source*)](https://www.socialmediatoday.com/news/13-fascinating-facts-about-reddit-infographic/523516/). Many people rely on reddit to understand more about a particular topic through subreddit. Reddit consistently gains momentum due to its constant support from the community who actively contributes information and opinions to the subreddits that they like. Subreddit covers a wide range of topics, from finance, politics to gaming and memes. Also, people can just subscribe to the subreddits and they will be continuously updated with discussions pertaining to the topics. Those subreddits are also well-maintained by reddit moderators to ensure posts are proper and contain no bullying or harassment.

As such, this project aims to understand the differing gaming aspects between two subreddits through the power of Natural Language Processing (NLP). The two subreddits are [DotA2](https://www.reddit.com/r/DotA2/) and [League of Legends](https://www.reddit.com/r/leagueoflegends/).



## Problem Statement
Due to the Covid-19 pandemic, many people has shifted to online activities to maintain relationship with their closed ones. One of the most popular online activities is gaming. Online gaming has since garnered more attention and has also been the core to many communities. The start of many popular online games are Dota2 and League of Legends, in which the games are free and require massive teamwork to win the game. Both games have been around since 2011 and 2009 consecutively, with Dota2 as the continuation of Dota (released in 2003) followed by its success. Even in 2022, both games are still in the top 20 most popular PC games in the world [(source)](https://newzoo.com/insights/rankings/top-20-pc-games).

Both DotA2 and LOL are Role-Playing Game (RPG) and each teammate needs to play a character and act as a certain role (top laner, jungler, mid laner, bottom laner and support). Each of the laners can also build their characters as carries, cores, gankers, etc depending on their items purchase and also the natural abilities of the characters.

Due to the many complex character abilities and strategies, DotA2 and LOL fanbase communities like to discuss their builds, items, skins, highlights of their matches as well as top competition team plays in reddit. Fun fact, DotA2 highest level of competition (The International 2021) has the largest prize pool in any esports tournament worldwide ever. It has the prize pool of \$40 millions, compared to Fortnite World Cup finals 2019 which is \$15 millions. 

As a junior data scientist in Twitch, i was tasked to create a feature of an internal ambitious project. The team has been developing news feed in Twitch and one of the category is gaming. I was asked to give insights of two similar games and create a classification machine learning model for future posts so Twitch streamers/users can get personalised news feed with correct tags on the feed. Additionally, this could also gives the business development/ marketing team to design sales & marketing campaigns that best meet the user's need.

Observing the popularity of DotA2, I decided to compare DotA2 posts vs League of Legends posts as both games are similar yet contrasting in nature.


 ## Approach
Below are the proposed approaches for this project
    
- Data Collection
    - Scrape two reddit posts using Pushshift API and *request* library
    - Combine posts together after each API pull

-  Data Cleaning and EDA
    - Clean selftext and title words by using regex, remove punctuations and stop words as well as tokenize, stem and lemmatize the texts
    - Using NLP through Count Vectorizer and TF-IDF Vectorizer to analyse the word frequency for both subreddits  

-  Machine Modelling & Selection
    - Utilization of pipelines to orchestrate the machine learning operations and allow a series of data transformations linkage to a measurable   modelling process
    - Different classification machine learning models development (Logistic Regression, Multinomial Naive Bayes, K-Nearest Neighbor as well as Random Forest Classifier) and compare them to choose the best model
    - GridSearchCV coupled with pipeline hyperparameter tuning to enable model accuracy enhancement
    - Top important words from each machine learning model understanding

## Summary & Conclusion
Below are a few key observations:

__Count Vectorizer method__

_Dota2_
- Subreddit generally centers around tournaments, as seen from the word Stockholm, referring to ESL one in Stockholm happened 12 May -22 May 2022
- Also, TI (The International) and DPC (Dota Pro Circuit) refer to the top tournaments and placements for top teams
- MMRs are also the top words as people talk about their own ranked matches or pro players rank matches


_League of Legends_
- Subreddit centers around gameplay & game highlights as people talk about ability, challenge, spell , ultimate.
- The community talks a bit of strategy as shown in the word adc (Attack Damage Carry) and bot (Bottom lane)
- Only MSI ( Mid-Season Invitational) competition is in the frequent word, unlike Dota2 with many competitions in the word list

Both games publisher (Valve for Dota2 and Riot for League of Legends) are in the top words list which is expected.

Surprisingly, only a small portion of hero names from each game are mentioned.
- For Dota2, only 'spirit' is mentioned. However, 'spirit' can refer to 4 heroes e.g. 'Ember Spirit', 'Void Spirit', 'Storm Spirit' , 'Earth Spirit' and 'Spirit Breaker'. 
- For League of Legends, only teemo is mentioned in the list.

__TF-IDF Vectorizer method__

_Dota2_
- Similar observations are observed as compared to count vectorizer. Dota2 subreddit still centers around tournament talks
- However, there are some topics with more weightage that are more discussed e.g. arcanum and immortal which are the items rarity as well as hero names


_Leauge of Legends_
- League of legends community still discusses about gameplay, ability and strategies
- However, some topics with more weightage occurred e.g. hero names and tournament jargons (Saigon Buffalo and MSI rumble)

For the best model, __Count Vectorizer - Multinomial Bayes__ is used based on the following reasons:
- Provides the best testing accuracy score (88.6%)
- While TF-IDF theoretically results in a better model performance comparing to Count Vectorizer due to its weightage on the presence of each token relative to the frequency of the posts, Count Vectorizer has a faster runtime (27 secs vs 1.2 mins) with similar test accuracy score
- Multinomial Bayes has lower overfitting values compared to other models including logistic regression
- Multinomial Bayes provides interpretibilty in which insights can be easier derived based on the words importance to classify the subreddits

Observations for __Count Vectorizer - Multinomial Naive Bayes__ model (*Top 20 word predictors can be referred to the charts in the notebook*):
- Tournament related events (Stockholm, ESL, DPC) are very strong indicators that a post belongs to DotA2 subreddit. It is almost as important as the hero (Maokai) in League of Legends.
- Furthermore, DotA2 team names (Gaimin, Betboom, Tundra, BeastCoast,  Yatoro and FTX) are also important keywords for classifying DotA2 subreddit
- Notably also observed that only 1 hero (Underlord) is a key predictor for DotA2 while there are more heroes (Kled, Ziggs, Bard, Tryndamere, Jax, Lux and Senna) are identified as key predictors for League of Legends
## Limitations & Future Work
There are a few limitations that were noted:
- Extra stop words are hard to be identified in a large scale text dataset. This requires manual identification of stop words removal
- Better data cleaning steps can be introduced to remove heroes names and unique terms in each subreddit to enable a more granular model
- A balance is also needed to ensure non-excessive overlapping words between subreddits
- Faster resources , i.e super computer is preferred to enable a wider range of hyperparameter tuning.

For future work, the team will pull data sources from other groups of sites, i.e. Twitter, Meta and Instagram to enable sources diversification. For better understanding, the team will also check on the misclassified posts and further enhance the accuracy score. In addition, feature additions will also be done in terms of flagging and removing unusual posts (spams, profanities, etc). Also, sentiment analysis feature can be added to provide game developers on real-time insights regarding sentiments of their games. Thus, they can plan and fix their games ahead of time whenever their games start to potray negative sentiments. On the other hand, extra analysis can also be provided to streamers to check what time each game has the highest traffic posts. This could potentially give insights to streamers on the best time to stream as the game community might be most active on that particular time and potentially gaining more views.
