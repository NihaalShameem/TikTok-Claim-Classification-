# TikTok-Claim-Classification
## Project Overview 
The TikTok data team wants to develop a machine learning model to assist in the classification of claims for user submissions. This means to determine wheter a video was a claim or of opinion based. 
## Problem
Videos on TikTok recieve a large number of user reports for a lot of different reasons. This leads to all videos not being able to be reviewed by a human moderator. Videos that make claims (as opposed to opinions) are much more likely to contaim content that violates the platform's term of service. TikTok seeks to a way to identify videos that make claims to prioritize them for review. 
## Solution 
We ended up going through many stages that included `data preperation, data cleaning, A/B Testing, and lastly builiding multiple models` that will help predict wheter videos were of claims or opinions.

## Data Preperation
I looked over the classification dataset, aiming to seek out relationships between variables. The ask for a classification of user claims, I looked at counts of claims and opinions in order to understand the count of each type of video content. <br>
The impact of the analysis is to be determined in the next steps. Two variabls were found that could be considered for future models, the `video_duration (in seconds)` and the `video_view_count`. After looking at the dataset, the variable `claim_status` seemed to be of the most use given the ask of the project. Below, we see the important point of analysis to understand the variable. <br>
![image](https://github.com/user-attachments/assets/300d39b3-ddd1-42b1-af4c-b165ffcf28cf)
### Engagement Trends 
I saw viewer engagment with each video within the claim and opinion status. The count of views was looked at to better understand the engagement. The mean and median below show the association between the `video views` and the `claim status`. <br>
**Claims:**
Mean view count claims: 501029.45
Median view count claims: 501555.0
<br>
**Opinions:**
Mean view count opinions: 4956.443
Median view count opinions: 4953.0

### Key Insights 
- There is only a slight difference between opinions and claims. With this information we can proceed knowing there is an equal amount of claims and opinions in this dataset.
- Now that we know the key variables to be focused on and the initial analysis we can go forward with the process of exploratory data analysis.

## Data Exploration
During this stage I examined the count frequencies, distribution, mean and median values, outliers, missing data, and much more. <br>
I also created scatter plots where I analyzed correlation between variables especially between the variable `claim_status` and others. <br>
Coming out of exploring the data I want to further analyze attributes of claims and of opinions. Also, would like to know other variables <br>
that might be of use to me understanding the data. My upmost interest of my client would be what variables or data would be most useful <br> 
in predicting our `claim_status`.

## Statistical Testing (A/B Test) Results
In this section of the project I am trying to understand the relationship `video_view_count` and `verified_status ` as video_view_count was one of the variables we wanted to dive deeper into due to it having one of the upmost value to the project ask. <br>
To analyze the relationship we will build a **hypothesis test**. 
### Details 
The first approach taken was to observe the mean values of `video_view_counts` for each group in the `verified_status` variable within our dataset. <br>
From examning the findings it was found that **unverified** accounts had a mean of ***265,663 views*** while **verified** accounts had a mean value of ***91,439 views***. <br>
![image](https://github.com/user-attachments/assets/80a5095e-d65c-495e-b5c9-377e9bf1adc1) <br>
The second approach was a **two-sample t-test**. The hypotheis test proved that the original findings were statisticall significant, showing that the differences in the sample data is due to an actual difference in the population means.
### Key Insights 
- This analysis shows that there is a statistically significant difference in TikTok videos posted by verified and unverified user accounts.
- These results suggest there might be behavioral differences between verified and unverified accounts.
- It would be interesting to investigate the root cause of these differences. For example, we could ask: <br>
        - Do unverified accounts post more engaging content and is that content a claim or opinion? <br>
        - Are unverified accounts associated with spam bots that help increase view counts?
  ### Next Steps
  I would move forward building a **regression model**  on `verified_status`. <br>
  A regression model for `verified_status` can help understand user behavior in the group of verified users. <br>
  Then, it can be applied to deem results from a classification model that will be created later on. 

## Regression Analysis
### Overview
The TikTok team end goal is to build a model that helps in the classification of claims for user submission. In an earlier project we observed that if a user was verified they were most likely to post an opinion based video.
Since the end goal is to predict claims or opinions, it is important to predict user behavior of verified account types which tend to post more opinions. Based on that information, we will build a ***logistic regression*** model that
predicts `verified_status`.
### Project Status
We included the variable `verified_status` in our model because we noticed a correlation between whether an account is verified and the type of video content it shares. Since we are trying to predict outcomes using this kind of data, a ***logistic regression*** model is a good fit, as it works well for data that falls into different categories (like whether an account is verified or not). <BR>
**A LOOK AT THE MODEL RESULTS** <br>
The logistic regression model achieved a precision of 68% and a recall of 65% (weighted averages). This model achieved an f1 accuracy of 64%. These results help us determine key insights on video features written in the "key insights" section. <br>
### Key Insights 
![image](https://github.com/user-attachments/assets/7c7dd140-87f5-4eae-8146-a89831fb2151) <br>
Based on the estimated model coefficients from the logistic regression, longer videos tend to be associated with higher odds of a user being verified. Other video features above have small estimated coefficients in the model, so their association with verified status is not very large. As a result we see that besides seem to not be in association with verified status. <br>

**CONFUSION MATRIX FOR LOGISTIC REGRESSION MODEL** <BR>
![image](https://github.com/user-attachments/assets/fe6f76ec-77a3-4acb-a075-38c521f47d41) <br>
*The upper-left displays the number of videos posted by unverified accounts. The upper-right displays the number of videos posted by unverified accounts. Lower-left displays the number of videos posted by verified accounts and lower-right displays the number of videos posted by verified accounts.*

## Machine Learning Model Outcomes (Classification Model)
### Overview
Previously, we investigated that video engagement levels were high suggestives as either claims or opions. This gives us confidence that this model will meet all performance requirements. <br>
### Solution to the Original Problem
I built a tree-based classification model, more specifically a random forest model. The model was used to predict on a hold-out validation dataset, and final model selection was determined by the model with the best recall score. The final model was used to scoe a test dataset to estimate future performance. <br> 
### Insights
The Random Forest Model perfomed very well ! The models recall score was 0.995. <br>
Performance on the test holdout set showed near perfect scores, with only 5 miscalculated samples out of a total 3,817 ! <br>
The analysis showed exactly like previous projects that the primary predictors, were all related to video engagement levels. `Video_view_count, share_count, and download_count accounting for almost all predictive signal in the data. Based on these results, we can come to conclusion that videos with higher user engagement levels were much more likely to be claims. <br>
![image](https://github.com/user-attachments/assets/19a04d6f-db38-48db-94d7-7db56b814cf7) 
![image](https://github.com/user-attachments/assets/c82570f1-803c-4434-945b-7c164d1525b7)


