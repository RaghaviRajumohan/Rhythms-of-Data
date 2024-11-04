
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
  - **Insert Image**: ![Correlation Heatmap](assets/Corr_Plot.png)
- **Histogram and Density Plots**: Provided insights into data distributions for variables such as `Acousticness`, `Liveness`, and `Speechiness`.
  - **Insert Image**: ![Feature Distribution](assets/histogram_density.png)
- **Scatter Plots**: Assessed linearity between `log_Stream` and key predictors, highlighting non-linear patterns for many variables.
  - **Insert Image**: ![Scatter Plots](assets/scatter_plots.png)

### 3. Feature Selection
Using Boruta SHAP and Variance Inflation Factor (VIF) analysis, we identified significant predictors:
- **Top Features**: `log_Duration_ms`, `log_Comments`, `Valence`, `Danceability`, `Liveness`, and `Speechiness`.
- **Variables Removed**: High collinearity led to the removal of `log_Likes` and `log_Views`.

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
