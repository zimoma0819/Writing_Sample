# TikTok User Claims/Opinions Classification Project

## Project Overview
The goal of this project is to develop a predictive model that can determine whether a TikTok video contains a claim or offers an opinion. The models that were constructed and evaluated were XGBoost and random forest models. The final random forest model had consistently high precision, recall and f-1 scores, allowing identification of the most important features used for differentiating claims from opinion-type videos. Based on the model, user engagement data such as each video's views, likes, shares and downloads were the most important features used for predicting the claim status of TikTok videos.

## Business Understanding
TikTok users have the ability to submit reports that identify videos and comments that contain user claims. These reports identify content that needs to be reviewed by moderators. The process generates a large number of user reports that are challenging to consider in a timely manner. By constructing and subsequently deploying a high-performing video classification model, the user reports can be sorted by priority based on whether the video is likely to contain a claim or opinion. This allows for efficient review of the videos listed as claims by moderators and helps to reduce the piling backlog of user reports.

## Data Understanding
The data used in this project is a synthetic dataset made by the TikTok team for the Google Advanced Data Analytics Professional Certificate Course. A copy of the dataset can be found in the files section of this repository. It contains 19382 rows and 12 columns with each video representing each row and various features such as user engagement data or transcription texts representing the columns. There were 298 rows that contained missing values in the dataset and these affected rows were dropped as they only constituted a minor fraction of the data available. There were no duplicated rows and the class balance of videos containing claims or opinions was approximately equal so neither up nor down-sampling was required to balance the dataset. Unnecessary columns such as video ID, and number were dropped while categorical columns like claim_status, author_ban_status and verified_status were encoded to numerical values. Feature engineering was performed as well, on the column 'video_transcripted_text' to extract a new feature 'text_length' in order to derive numerical values that can be used as a potential feature.

## Modelling and evaluation
A random forest comprising 75 trees was used as the champion model to predict whether a video contained a claim or offered an opinion. The barplot below shows that in agreement with the prior EDA conducted, user engagement-related features such as views, likes, shares, downloads and comments were among the most important features in determining whether a video contains a claim.

![image](https://github.com/user-attachments/assets/2ba0f79d-151a-4c86-b8af-8bc002866439)

Additionally, the confusion matrix below shows that out of the 3817 rows in the test holdout data, there were only 3 false positives and 16 false negatives.

![image](https://github.com/user-attachments/assets/50fdf759-c0b4-4900-8cc2-95a9ba83e0a9)

## Conclusion
The model constructed was able to successfully classify videos by their claim status and the most predictive features were all related to the user engagement levels associated with each video. Initial data inspection and exploratory data analysis also identified close correlations between these engagement features and the claim status of videos. Statistical testing and regression modeling were also performed to derive further insights from the data and are explained in greater detail in the various notebooks listed in this repository. Lastly, the 'video_transcription_text' feature was dropped before the construction of the models as it was text-based and not a categorical feature that could be encoded easily. However, we could explore the use of natural language processing such as the CountVectorizer algorithm to transform it into a usable feature that may enhance the performance of the models.
