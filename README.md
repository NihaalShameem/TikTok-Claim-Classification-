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

