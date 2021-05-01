# Predicting Reddit Comment Karma 
By :- Ankita BHATTACHARYA, M2 Eco-Stat, TSE
Kaggle MAE score (public leaderbord): 9.38 
Date created : 08.04.2021

This readme document explains the objective of this project and the methods used to execute it. The term project for Web Mining consisted in predicting the karma or score (upvotes-downvotes) of 1016458  Reddit comments for an OP in the AskReddit subreddit which is one of the most popular subreddits of Reddit.

- I. Constituents of the folder
The zip file contains the two notebooks
  - 1. Part I : Feature_Engineering
  - 2. Part II : Prediction



-   II. Data & Notebooks
The database "comments.csv" was our principal database containing over 4 million reddit comments, downloaded from Kaggle. 
Two .ipnyb notebooks were executed on the Jupyter Notebook interface on Python3 kernel are used to arrive at the final result 
These must be run one after the other to obtain  the final result. 

- III. How to install libraries required 
``` !pip install xgboost
    !pip install parfit
```


- IV. Explaining the choice of features
As the name suggests, the first notebook contains the extraction of features based on :
  -  Text content
  - Time of comments
  - Network mining

The list of the 43 features are given below :   
    - A. Content based features : (Stylometric characteristics)
      -1. Length of the comment in words
      -2. Count words beginning with capital letters
      -3. Count number of exclamations
      -4. Question marks
      -5. Punctuation count
      -6. Number of 'I's used in the comment
      -7. Number of urls
      -8. Associated subreddits

I added these two features to improve the model:
      - 9. Lexical Diversity
      -10. Number of times comment references another comment

Text Mining (LDA) features
20 features

B. Time based features

1. Time difference between OP and other comments
2. Hour of the comment
3. Day of the comment
4. Time between the OP's first comment & the others by thread


C. Network mining based features
(Structural characteristics)
1. Reply to first comment : Earlier comments get more traction, and so do the replies to these comments 
2. Thread popularity : calculating the length of the thread, or the number of unique authors in the link id
	Comment-Comment features : How responding to which comment gives you a bigger score
3. Comment depth : Calculating the comments made in response to a thread
4. Number of neighbours : Calculating the neighbours for each thread 
	Author-Author features : Interaction between users and its impact on the score
5. Degree centrality
6. Betweenness centrality
7. Eigenvector centrality 
8. Score by parent_id :Obtaining the score of comments by the parent_id or the score of the post to which the comments are a reply to.
9. Number of comments made by author


V. Model Used
- XGBoost
The metric we use to evaluate the performance of the  models is the MAE. 
- Tuning of hyperparameters using parfit was used. 

VI. Conclusion
Structural and time based features were more important to the model than text based features

