# citizen_engagement
Machine Learning classification model for citizen engagement in smart-city, based on my 3 case studies Taipei (Taiwan), Tel Aviv (Israel) and Tallinn (Estonia).

this repository contains : 
- ERD citizen_engagementDB : a png sketch of the Entity-Relationship Diagram of the database citizen_engagementDB.
- citizen_engagementDB : a SQL database ready to implement, containing surveys, interviews and twitter datasets from Taipei, Tel Aviv and Tallinn.
- ML citizen engagement : a ipynb notebook containing SQL and python queries to the database in order to build a Classification Model of Machine Learning. 
- allsurvey_visuals : a twbx Tableau file displaying data visualisations of the survey records. 
- MACHINE LEARNING Classification Model for Citizen engagement in Smart-City : slide presentation of my model, with first results and argumentation, are accessible by this link =>  https://docs.google.com/presentation/d/1UDIOtwIuhwywTpZtFp4No7JwL8oTIxyd5wI3-UIkr2U/edit?usp=sharing
- a video record of the presentation can be watched on youtube https://youtu.be/DHijjFp7M0U 



MACHINE LEARNING : A classification model based on Citizen engagement in Smart-City. 

GENERAL : 
I want my Machine Learning Model to classify cities depending on the citizen engagement dynamic around their digital transformation.

To do so, I will have to determine what makes a highly engaged citizen, and at a city scale, what makes a highly engaging city.
I am building my model from 3 case study cities : Taipei (Taiwan), Tel Aviv (Israel) and Tallinn (Estonia).   In a later step, I plan to automate the process of :  - data collection (similar to the ones collected for my case studies)  - data analysis
- cities classification 
- reports production (frames of visualisation to fill with new cases)


DEFINITION : 
A citizen highly engaged in the digital transformation of its city can be defined as following :
uses social media and internet as a media source to form its opinion
meets other citizens online 
share its opinion
wish to engage more
=> these values are contained in the survey 

A citizen highly engaged on Twitter in the digital transformation of its city will :
publish a significantly higher number of tweets than the average twitter users
be active in the last monts
=> these values are contained in the tweet record

This is what it needs AT LEAST, and I will complete this model later, with more values from survey, twitter and interview, but also from other data sources. 
A highly engaging city will have a significant number of highly engaged citizens, and also some open data repositories to define later. 

The Machine Learning Classification Model will be built on a highly engaged criteria (T/F) or on an engagement score (FLOAT%) >= a threshold value. 
y = conditions which define a highly engaged citizen
X = conditions which should influence someones engagement 

If conditions X are true, and y true or >= threshold value, the citizen can be considered as a highly engaged one. Will need to test and refine the model with other columns in X that should not influence engagement. 




TO IMPROVE THE MODEL :

break the multiple answers string to single values (check string_split to put them in separate columns or ideally rows if the primary key is not an issue) => maybe not needed to break if possible to count single answers by REGEX function.

survey_date, interview_date, tweet_date must be reformatted to integrate in SQL tables
replace #N/A by "" in the whole datasets

Upload the stakeholders datasets in the tweet table. 

find the name of my agent_id based on twitter_profile, interview and survey email (not shared on this database for privacy issue)
Add it to agent table

find the twitter_profile of my interview and survey participants. 
add it to agent table

drawing a diagram of the process which assesses an agent a higly_engaged level :
if A is true and B is true and C is true and D is not true, and E or F is true then high. 
containing all concerned columns and potentially up to receive more. 

bring sentiment analysis to give the tweets a category between POSITIVE - NEUTRAL - NEGATIVE. 
This value can be stored in a column tweet_sentiment. 
Calculate the % of each tweet_sentiment for the whole dataset (= mean)
Calculate the % of each tweet_sentiment by city_id 
Compare the % of each tweet_sentiment by city_id to the mean (= standard deviation)

Check if possible to calculate a grading sentiment intensiveness (FLOAT number) 
If possible, store it in tweet_intensiveness and bucket into engagement_level, in order to identify the highly_engaged citizens (T/F) based on a threshold value to be defined. 
(BE CAREFUL : being highly_engaged do not means having a positive sentiment only) => calculate engagement_level with a NEUTRAL category around the 50% of intensiveness OR => with tweet_sentiment NEUTRAL = tweet_intensiveness 0%, tweet_sentiment POSITIVE having tweet_intensiveness +(0 to n)% and tweet_sentiment NEGATIVE having tweet_intensiveness -(0 to n)%

This sentiment_analysis or sentiment_intensiveness data, is my test/train data source for y everything else is X including City. 
A global_engaging_score can be calculated by combining different parameters from citizens engagement_score / highly_engaged (T/F).

A global_sentiment_score can be calculated by combining different parameters from tweet_sentiment AND/OR tweet_intensiveness.
A global ranking will be processed on the cities based on their global_engaging_score and global_sentiment_score.
