
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

In developing a regression model to predict `log_Stream`, we explored various model iterations, including the use of Mallows' \( C_p \) criterion to guide model selection. Mallows' \( C_p \) is a model selection statistic that helps identify models that provide a good balance between accuracy and simplicity. Lower \( C_p \) values indicate models that are closer to the true model, with minimal bias and variance.

#### Step-by-Step Process

1. **Baseline Model**:
   - We ran a regression of all the selected variables and applied Mallows' \( C_p \) criterion to select our baseline model. This model included only the key features identified through Boruta SHAP and VIF analysis.
   - The baseline model served as a foundation for comparison, allowing us to assess potential improvements by introducing interaction and quadratic terms.
   - **Formula of the Baseline Model**:
     
     $$
     \text{log\_Stream} = \beta_0 + \beta_1 \cdot \text{Acousticness} + \beta_2 \cdot \text{Liveness} + \beta_3 \cdot \text{Speechiness} + \beta_4 \cdot \text{Instrumentalness\_logit} + \beta_5 \cdot \text{Licensed} + \beta_6 \cdot \text{log\_Duration\_ms} + \beta_7 \cdot \text{Valence} + \beta_8 \cdot \text{log\_Comments} + \beta_9 \cdot \text{Album\_single}
     $$

     where:
     - \( \beta_0 \) is the intercept.
     - \( \beta_1, \beta_2, \dots, \beta_5 \) are coefficients for each predictor.
     - \( \epsilon \) is the error term.

   - Initial metrics:
     - **R-squared**: 28.3%
     - **Adjusted R-squared**: 27.6%
     - **Mallows' \( C_p \)**: Higher than optimal, suggesting further refinements were needed.

2. **Adding Interaction Terms**:
   - Interaction terms were introduced to capture the combined effects of specific pairs of predictors on `log_Stream`.
   - **Tested Interactions**:
     - `log_Duration_ms * Danceability`
     - `Valence * Liveness`
     - `log_Comments * Speechiness`
   - **Evaluation**:
     - Each interaction term was evaluated individually using Mallows' \( C_p \), with lower \( C_p \) values indicating improved fit.
     - `log_Duration_ms * Danceability` and `Valence * Liveness` were significant and reduced \( C_p \), enhancing the model's explanatory power.
     - **Updated Formula**:

       \[
       \text{log\_Stream} = \beta_0 + \beta_1 \cdot \text{log\_Duration\_ms} + \beta_2 \cdot \text{log\_Comments} + \beta_3 \cdot \text{Danceability} + \beta_4 \cdot \text{Valence} + \beta_5 \cdot \text{Liveness} + \beta_6 \cdot (\text{log\_Duration\_ms} \cdot \text{Danceability}) + \beta_7 \cdot (\text{Valence} \cdot \text{Liveness}) + \epsilon
       \]

3. **Adding Quadratic Terms**:
   - Quadratic terms were added to account for non-linear relationships between certain predictors and `log_Stream`.
   - **Tested Quadratic Terms**:
     - `Danceability^2`
     - `Valence^2`
   - **Evaluation**:
     - Including `Danceability^2` and `Valence^2` further reduced Mallows' \( C_p \) and improved model fit, indicating that moderate values of these variables were optimal for popularity.
     - **Final Formula**:

       \[
       \text{log\_Stream} = \beta_0 + \beta_1 \cdot \text{log\_Duration\_ms} + \beta_2 \cdot \text{log\_Comments} + \beta_3 \cdot \text{Danceability} + \beta_4 \cdot \text{Valence} + \beta_5 \cdot \text{Liveness} + \beta_6 \cdot (\text{log\_Duration\_ms} \cdot \text{Danceability}) + \beta_7 \cdot (\text{Valence} \cdot \text{Liveness}) + \beta_8 \cdot \text{Danceability}^2 + \beta_9 \cdot \text{Valence}^2 + \epsilon
       \]

#### Final Model Performance
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
  - `Danceability^2` and `Valence^2`: Suggest a non-linear relationship, where moderate values of these features may be optimal for popularity rather than extremely high or low values.

The final model provides a robust and interpretable framework for predicting song popularity on Spotify, balancing simplicity with predictive power.

<div align="center">
  <!-- Placeholder for Model Plots -->
  <img src="Assets/model_plots_placeholder.png" alt="Model Diagnostic Plots" width="500" style="display: block; margin-top: 20px; margin-bottom: 20px;">
</div>
### 5. Findings and Recommendations
The analysis highlighted social engagement (`log_Comments`) and track characteristics (`Danceability`, `Valence`) as key drivers of popularity. Industry professionals can use these insights to tailor song attributes for optimal audience engagement.

## Conclusion
This project successfully developed a model to predict music popularity, providing actionable insights for music production and marketing. Further enhancements could include integrating additional social engagement metrics or exploring non-linear modeling techniques for improved accuracy.
