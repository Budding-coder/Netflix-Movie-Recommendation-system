# Netflix-Movie-Recommendation-system

## Problem Description

Netflix is a online repository where we can watch videos, movies, documentaries etc. Netflix is all about connecting people to the movies they love. 
To help customers find those movies, they developed world-class movie recommendation system: CinematchSM (Cinematch system is internally built by Netflix). 
Its job is to predict whether someone will enjoy a movie based on how much they liked or disliked other movies. 
Netflix use those predictions to make personal movie recommendations based on each customer’s unique tastes. 
And while Cinematch is doing pretty well, it can always be made better.
Metric used is RMSE - Root Mean Squared Error

Now there are a lot of interesting alternative approaches to how Cinematch works that netflix haven’t tried. 
Some are described in the literature, some aren’t. We’re curious whether any of these can beat Cinematch by making better predictions. 
Because, frankly, if there is a much better approach it could make a big difference to the customers and the business.

## Problem Statement

Netflix provided a lot of anonymous rating data, and a prediction accuracy bar that is 10% better than what Cinematch can do on the same training data set. 
(Accuracy is a measurement of how closely predicted ratings of movies match subsequent actual ratings.) 

## Sources

https://www.netflixprize.com/rules.html</li>
https://www.kaggle.com/netflix-inc/netflix-prize-data</li>
Netflix blog: https://medium.com/netflix-techblog/netflix-recommendations-beyond-the-5-stars-part-1-55838468f429 (very nice blog)</li>
surprise library: http://surpriselib.com/ (we use many models from this library)</li>
surprise library doc: http://surprise.readthedocs.io/en/stable/getting_started.html (we use many models from this library)</li>
installing surprise: https://github.com/NicolasHug/Surprise#installation </li>
Research paper: http://courses.ischool.berkeley.edu/i290-dm/s11/SECURE/a1-koren.pdf (most of our work was inspired by this paper)</li>
SVD Decomposition : https://www.youtube.com/watch?v=P5mlg91as1c </li>

## Real world/Business Objectives and constraints 

### Objectives:

1. Predict the rating that a user would give to a movie that he/she has not yet rated.
2. Minimize the difference between predicted rating given by algorithm and actual rating given by user (RMSE and MAPE).
3. RMSE - Root Mean Squared Error , MAPE - Mean Absolute Percentage Error.
4. Rating values will be between 1 to 5.
5. This case study is like regression problem and we can pose it as both, regression problem as it has rating(class Y) 
values from 1 to 5 and can also pose as a recommendation problem as we are trying to recommend movie Mj to a user Ui. 

### Constraints:

1. Some form of interpretability. We should understand why the model is recomending particular movie, 
and user also should understand why they are being recommended a movie. This is important constraint.
2. We may think that low-latency should be there for this recommendation , but netflix does not compute the movie recommendations right at the moment when the user logs-in.
It will pre-compute all these movie recommendations for every user and put these recommendations in hash table or look-up table.
3. As soon as the user log-in, it will show the pre-computed movie recommendations to the user . 
As many users watch minimum number of movies a day, netflix can take hours and compute the movie recommendations for each day, and show to the users when they log-in. 
4. So these recommendations are good and so there is no explicit low latency requirement as recomendations can be pre-computed and there is no need to compute in milli-sec. 

## Data Overview 

Get the data from : https://www.kaggle.com/netflix-inc/netflix-prize-data/data </p>
<p> Data files : 
<ul> 
<li> combined_data_1.txt </li>
<li> combined_data_2.txt </li>
<li> combined_data_3.txt </li>
<li> combined_data_4.txt </li>
<li> movie_titles.csv   -- It has movie id and movie name</li>
</ul>
<pre>  
The first line of each file [combined_data_1.txt, combined_data_2.txt, combined_data_3.txt, combined_data_4.txt] contains the movie id followed by a colon. 
Each subsequent line in the file corresponds to a rating from a customer and its date in the following format:

CustomerID,Rating,Date

MovieIDs range from 1 to 17770 sequentially.
CustomerIDs range from 1 to 2649429, with gaps. There are 480189 unique users.
Ratings are on a five star (integral) scale from 1 to 5.
Dates have the format YYYY-MM-DD.

## Type of Machine Learning Problem

1. For a given movie and user we need to predict the rating would be given by him/her to the movie. 
2. The given problem is a Recommendation problem . There are multiple approaches for this problem like similarity based approaches like,
user-user similarity , item-item similarity ,etc. , Matrix Factorization approaches  
3. It can also seen as a Regression problem. As ratings rij's are values between 1 to 5 . These are Yi's. 
And we can get Xi's from the recommendation system  matrix dataset of movies and users. 
4. So we will use concepts from recommendation and matrix factorixation like SVD, User-user similarity, 
movie-movie similarity and concepts of regression like XGBoost

### Performance metric

1. Mean Absolute Percentage Error: https://en.wikipedia.org/wiki/Mean_absolute_percentage_error
2. Root Mean Square Error: https://en.wikipedia.org/wiki/Root-mean-square_deviation

### Main objective is :-

1. Minimize RMSE - Root Mean Squared Error
2. Try to provide some interpretability (understanding of why model gave particular recommendations).

### Libraries used :

1. sklearn - Machine learning library
2. seaborn, matplotlib.pyplot, - Visualization libraries
3. numpy, scipy- number python library
4. pandas - data handling library
5. XGBoost - Used for making regression models
6. Surprise - used for making recommendation system models




















