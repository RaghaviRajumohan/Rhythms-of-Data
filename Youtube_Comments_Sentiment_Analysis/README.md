<img src="Assets/doechii.png" alt="Doechii YouTube Comment Sentiment Analysis" width="800" style="display: block; margin: 10px auto 20px auto;">



# Doechii YouTube Comment Sentiment Analysis

This project analyzes the sentiment of comments on Doechii's YouTube music videos, aiming to uncover audience engagement and predict view counts based on sentiment patterns. By applying natural language processing (NLP) techniques and regression modeling, this project provides insights into fan sentiment and its potential impact on video performance.

-- 

## Project Overview

- **Objective**: 
   - Analyze the sentiment of YouTube comments to understand the audience's emotional response to Doechii's videos.
   - Leverage sentiment scores and engagement metrics to predict video view counts.
- **Data Source**: 
   - YouTube API for extracting comments, video statistics, and engagement data from Doechii's channel.

-- 

### Key Python Packages and Tools for YouTube Comment Sentiment Analysis

**Data Extraction and API Interaction:** ![Google API Client](https://img.shields.io/badge/Google%20API%20Client-4285F4?style=flat-square&logo=google&logoColor=white)

#### Data Manipulation and Cleaning: ![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)  ![NumPy](https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white)

#### Natural Language Processing (NLP) and Sentiment Analysis: ![NLTK](https://img.shields.io/badge/NLTK-85DDFF?style=flat-square&logo=python&logoColor=white) ![VADER Sentiment Analyzer](https://img.shields.io/badge/VADER%20Sentiment%20Analyzer-FF4500?style=flat-square&logo=python&logoColor=white) ![re](https://img.shields.io/badge/re-007ACC?style=flat-square&logo=python&logoColor=white)

#### Machine Learning and Classification: ![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-F7931E?style=flat-square&logo=scikit-learn&logoColor=white) ![CountVectorizer](https://img.shields.io/badge/CountVectorizer-3776AB?style=flat-square&logo=scikit-learn&logoColor=white) ![Resampling (Scikit-Learn)](https://img.shields.io/badge/Resampling-FF69B4?style=flat-square&logo=scikit-learn&logoColor=white) 

#### Data Visualization: ![Matplotlib](https://img.shields.io/badge/Matplotlib-007ACC?style=flat-square&logo=matplotlib&logoColor=white) ![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=flat-square) ![WordCloud](https://img.shields.io/badge/WordCloud-FFA07A?style=flat-square&logo=python&logoColor=white) 

#### Statistical Modeling and Regression Analysis: ![Statsmodels](https://img.shields.io/badge/Statsmodels-00A3E0?style=flat-square) ![Patsy](https://img.shields.io/badge/Patsy-003366?style=flat-square) 

#### Environment Management: ![Python-dotenv](https://img.shields.io/badge/Dotenv-2CA5E0?style=flat-square&logo=python&logoColor=white) 

-- 

## Project Steps

### 1. Data Collection and Preprocessing

   - **Data Collection**: Extracted YouTube comments, likes, views, and other engagement metrics from Doechii's channel.
   - **Text Cleaning**: Removed emojis, URLs, special characters, and normalized text to enhance sentiment analysis accuracy.

### 2. Sentiment Analysis

   - Used the VADER sentiment analysis tool to score comments as Positive, Neutral, or Negative.
   - Customized VADER's lexicon to accurately capture slang and expressions common in fan comments.

   <img src="Assets/Sent_dist.png" alt="Sentiment Distribution" width="600" style="display: block; margin: 10px auto 20px auto;">
   

### 3. Visualizing Sentiment

   - **Sentiment Distribution**: Illustrated the distribution of positive, neutral, and negative comments.
   - **Word Clouds**: Created word clouds for positive and negative sentiments, highlighting common themes in fan feedback.
   
   <img src="Assets/word_cloud.png" alt="Positive and Negative Word Clouds" width="400" style="display: block; margin: 10px auto 20px auto;">
   

### 4. Regression Analysis

   - Performed a regression analysis using sentiment scores and engagement metrics (likes, comments) to predict video view counts.
   - Results indicate a significant relationship between sentiment and video performance, emphasizing the impact of audience perception on engagement.

<img src="Assets/regression.png" alt="OLS Regression Results" width="600" style="display: block; margin: 10px auto 20px auto;">

## Conclusion

This analysis highlights the role of sentiment in understanding audience engagement with Doechii's content. By combining sentiment analysis with regression modeling, we gain actionable insights into how fans perceive Doechii's music and how this influences viewership trends.

