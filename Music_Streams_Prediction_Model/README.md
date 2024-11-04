
# Music Streams Prediction Model

This project aims to analyze and predict song popularity based on attributes from Spotify and YouTube data. By leveraging diverse musical, technical, and social metrics, we sought to uncover factors influencing a song’s popularity, represented by the number of streams on Spotify. 

## Project Overview

- **Objective**: Analyze 26 variables across songs, including attributes like energy, tempo, and social metrics, to determine the key factors affecting music popularity.
- **Data Source**: Spotify and YouTube datasets capturing both musical attributes and engagement metrics.

## Project Steps

### 1. Data Loading and Preprocessing
- **Data Cleaning**: Handled missing values and reset indices after removal of nulls.
- **Feature Engineering**:
  - Created binary variables for categorical attributes like `Licensed` and `official_video`.
  - Transformed highly skewed variables (e.g., `Views`, `Likes`, `Comments`, `Stream`) using logarithmic transformations.
  - Standardized variables for uniform scale, essential for regression modeling.

### 2. Exploratory Data Analysis (EDA)

Key insights from EDA informed our understanding of the data distributions and correlations:

- **Correlation Heatmap**: Identified strong positive correlation between `Licensed` and `official_video`, suggesting possible redundancy.

     <img src="Assets/Corr_Plot.png" alt="Correlation Heatmap" width="400" style="display: block; margin: 10px auto 20px auto;">

- **Histogram and Density Plots**: Provided insights into data distributions for variables such as `Acousticness`, `Liveness`, and `Speechiness`.

     <img src="Assets/Density_Plots.png" alt="Density Plots" width="400" style="display: block; margin: 10px auto 20px auto;">

- **Q-Q Plots**: Examined the normality of various features to assess their distribution characteristics.

     <img src="Assets/qq_plots.png" alt="Q-Q Plots" width="400" style="display: block; margin: 10px auto 20px auto;">

 
- **Scatter Plots**: Assessed linearity between `log_Stream` and key predictors, highlighting non-linear patterns for many variables.
  
     <img src="Assets/Scatter_Plot.png" alt="Density Plots" width="400" style="display: block; margin: 10px auto 20px auto;">

### 3. Feature Selection
Using Boruta SHAP and Variance Inflation Factor (VIF) analysis, we identified significant predictors:
- **Top Features**: `log_Duration_ms`, `log_Comments`, `Valence`, `Danceability`, `Liveness`, and `Speechiness`.
- **Variables Removed**: High collinearity led to the removal of `log_Likes` and `log_Views`.

### 3. Feature Selection

To determine the most impactful features for predicting `log_Stream`, we used three main approaches:

1. **Boruta SHAP**: A feature ranking algorithm that leverages SHAP values to identify important variables based on feature importance.
2. **Variance Inflation Factor (VIF)**: Assessed multicollinearity among predictors. High VIF values indicate strong collinearity with other features, leading us to remove certain variables to enhance model stability.
3. **ANOVA**: Conducted to evaluate the significance of categorical variables in predicting `log_Stream` by examining F-values. The lower the p-value, the more significant the variable is in explaining variability in the target.

#### Selected Features
Based on the Boruta SHAP, VIF, and ANOVA analyses, we identified the following significant predictors: `log_Duration_ms`, `log_Comments`, `Valence`, `Danceability`, `Liveness`, and `Speechiness`. Variables with high collinearity (`log_Likes` and `log_Views`) were removed due to their high VIF scores.

#### Results Tables

- **Variance Inflation Factor (VIF) Scores**

  | Feature              | VIF       |
  |----------------------|-----------|
  | log_Likes            | 25.40     |
  | log_Views            | 18.21     |
  | log_Comments         | 6.53      |
  | Energy               | 3.51      |
  | Loudness             | 3.35      |
  | Acousticness         | 1.92      |
  | Danceability         | 1.65      |
  | Valence              | 1.59      |
  | Instrumentalness_logit | 1.51   |
  | Speechiness          | 1.14      |
  | log_Duration_ms      | 1.11      |
  | Liveness             | 1.07      |
  | Tempo                | 1.06      |
  | Key                  | 1.00      |

  Variables with a VIF score above 10, such as `log_Likes` and `log_Views`, were excluded due to high multicollinearity.

- **Boruta SHAP Ranking**

  | Feature               | Rank |
  |-----------------------|------|
  | Danceability          | 1    |
  | Energy                | 1    |
  | Loudness              | 1    |
  | Speechiness           | 1    |
  | Acousticness          | 1    |
  | Liveness              | 1    |
  | log_Duration_ms       | 1    |
  | Instrumentalness_logit| 1    |
  | log_Comments          | 1    |
  | Valence               | 2    |
  | Tempo                 | 3    |
  | Key                   | 4    |

  The Boruta SHAP algorithm highlighted variables with a ranking of 1 as the most important, such as `Danceability`, `log_Duration_ms`, and `log_Comments`.

- **ANOVA F-values for Categorical Variables**

  | Factor               | F-statistic     |
  |----------------------|-----------------|
  | Album_single         | 496.75         |
  | Licensed             | 215.58         |
  | official_video       | 185.62         |

  ANOVA results show that `Album_single`, `Licensed`, and `official_video` were statistically significant in predicting `log_Stream`, with `Album_single` having the highest F-statistic.

### 4. Model Development
Several regression models were tested using Ordinary Least Squares (OLS), with **Model 3** emerging as the best fit due to simplicity and low multicollinearity.
- **Final Model**: Excludes `Acousticness` for reduced complexity while retaining high predictive power.
- **Performance Metrics**:
  - R-squared: 34.5%
  - F-statistic: High significance level, confirming model reliability.
  - **Coefficients**: `log_Comments` and `log_Duration_ms` showed strong positive associations with `log_Stream`.

### 5. Findings and Recommendations
The analysis highlighted social engagement (`log_Comments`) and track characteristics (`Danceability`, `Valence`) as key drivers of popularity. Industry professionals can use these insights to tailor song attributes for optimal audience engagement.

## Conclusion
This project successfully developed a model to predict music popularity, providing actionable insights for music production and marketing. Further enhancements could include integrating additional social engagement metrics or exploring non-linear modeling techniques for improved accuracy.

## Visuals for README
Consider including the following graphs in the README:
1. **Heatmap** - Highlighting variable correlations, especially `Licensed` and `official_video`.
   - **Insert Image**: ![Heatmap](assets/heatmap.png)
2. **Histograms with Density Overlay** - For key attributes (`Acousticness`, `Danceability`, `Valence`).
   - **Insert Image**: ![Histogram Density Overlay](assets/histogram_density_overlay.png)
3. **Scatter Plots** - Visualizing relationships between `log_Stream` and predictors like `log_Duration_ms` and `Danceability`.
   - **Insert Image**: ![Scatter Plots](assets/scatter_plots_example.png)

## Installation and Usage

Clone the repository and install necessary dependencies:
```bash
git clone [repository link]
cd [repository name]
pip install -r requirements.txt
