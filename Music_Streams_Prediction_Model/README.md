
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

To determine the most impactful features for predicting `log_Stream`, we used three main approaches:

1. **Boruta SHAP**: A feature ranking algorithm that leverages SHAP values to identify important variables based on feature importance.
2. **Variance Inflation Factor (VIF)**: Assessed multicollinearity among predictors. High VIF values indicate strong collinearity with other features, leading us to remove certain variables to enhance model stability.
3. **ANOVA**: Conducted to evaluate the significance of categorical variables in predicting `log_Stream` by examining F-values. The lower the p-value, the more significant the variable is in explaining variability in the target.

#### Selected Features
 
  - Variables with a VIF score above 10, such as `log_Likes` and `log_Views`, were excluded due to high multicollinearity.

  - The Boruta SHAP algorithm highlighted variables with a ranking of 1 as the most important, such as `Danceability`, `log_Duration_ms`, and `log_Comments`.

 -  ANOVA results show that `Album_single` and `Licensed` were more statistically significant in predicting `log_Stream`, with `Album_single` having the highest F-statistic. `Offical_Video` was dropped to resolve multicollinearity with `Licensed`.

### 4. Model Development

In developing a regression model to predict `log_Stream`, we tested several iterations, including interactions and quadratic terms, to find the best fit. The final model (referred to as **Model 3**) was selected for its simplicity and minimized multicollinearity, while still achieving strong predictive performance.

#### Step-by-Step Process

1. **Baseline Model**: 
   - Initially, we used a simple **Ordinary Least Squares (OLS)** regression with all selected features identified through Boruta SHAP and VIF analysis.
   - The model served as a baseline to assess basic predictive power without any complex terms.
   - Initial metrics: 
     - **R-squared**: 28.3%
     - **Adjusted R-squared**: 27.6%

2. **Adding Interaction Terms**:
   - Interaction terms allow us to capture the combined effect of two predictors on `log_Stream`, which may not be obvious when considering predictors independently.
   - **Tested Interactions**: 
     - `log_Duration_ms * Danceability`
     - `Valence * Liveness`
     - `log_Comments * Speechiness`
   - **Evaluation**:
     - Each interaction term was tested individually to avoid overfitting.
     - The interactions `log_Duration_ms * Danceability` and `Valence * Liveness` significantly improved the model's fit, leading to a modest increase in **R-squared** to 31.2%.
     - The interaction term `log_Comments * Speechiness` was not significant and was excluded.

3. **Adding Quadratic Terms**:
   - Quadratic terms were included to capture any non-linear relationships between the predictors and `log_Stream`.
   - **Tested Quadratic Terms**:
     - `Danceability^2`
     - `Valence^2`
     - `log_Duration_ms^2`
   - **Evaluation**:
     - The inclusion of `Danceability^2` and `Valence^2` provided a better fit, capturing curvature in the relationship between these variables and `log_Stream`.
     - `log_Duration_ms^2` did not improve the model and was excluded.
     - This step increased **R-squared** to 33.5%, indicating improved model fit without substantial complexity.

4. **Final Model Selection (Model 3)**:
   - After testing interaction and quadratic terms, **Model 3** was selected as the final model.
   - **Final Model**: Excludes `Acousticness` due to its minimal contribution to predictive power and to reduce complexity.
   - Key predictors: 
     - Linear terms: `log_Comments`, `log_Duration_ms`, `Danceability`, `Valence`
     - Interaction terms: `log_Duration_ms * Danceability`, `Valence * Liveness`
     - Quadratic terms: `Danceability^2`, `Valence^2`

#### Performance Metrics
- **R-squared**: 34.5%, indicating that the model explains 34.5% of the variance in `log_Stream`.
- **Adjusted R-squared**: 33.8%, confirming that the model maintains explanatory power without overfitting.
- **F-statistic**: High significance level (p < 0.001), confirming the overall reliability of the model.
  
#### Model Coefficients and Interpretation
The final model coefficients showed notable associations with `log_Stream`:
- **Positive Associations**:
  - `log_Comments`: Higher values are associated with increased stream counts, emphasizing the impact of social engagement.
  - `log_Duration_ms`: Longer song durations have a positive effect on streams.
  - **Interaction** (`log_Duration_ms * Danceability`): Indicates that songs with higher danceability benefit even more from longer durations.
- **Curvature Effects**:
  - `Danceability^2` and `Valence^2`: Suggests a non-linear relationship, where moderate values of these features may be optimal for popularity rather than extremely high or low values.

The final model provides a robust and interpretable framework for predicting song popularity on Spotify, balancing simplicity with predictive power.

### 5. Findings and Recommendations
The analysis highlighted social engagement (`log_Comments`) and track characteristics (`Danceability`, `Valence`) as key drivers of popularity. Industry professionals can use these insights to tailor song attributes for optimal audience engagement.

## Conclusion
This project successfully developed a model to predict music popularity, providing actionable insights for music production and marketing. Further enhancements could include integrating additional social engagement metrics or exploring non-linear modeling techniques for improved accuracy.
