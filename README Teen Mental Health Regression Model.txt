LLM Teen Mental Health Regression Model 

Overview

Teen_Mental_Health_Regression_Model is a regression-based machine learning project built in Google Colab to analyze how digital habits influence teen stress levels. The model uses behavioral and lifestyle features such as screen time, social media usage, and sleep patterns to predict stress levels.

The workflow emphasizes:

Data cleaning and validation
	Outlier detection and removal
	Feature transformation
	Robust regression modeling
	Metric validation (both manual and library-based)
==========================================================================================================================================

Dataset

Source: Digital Habits vs Mental Health Dataset

Platform: Kaggle
	Format: CSV
	Domain: Teen digital behavior and mental health
Key Features
	screen_time_hours – Daily screen usage
	social_media_platforms_used – Number of platforms used
	hours_on_TikTok – Time spent on TikTok
	sleep_hours – Daily sleep duration
	mood_score – Self-reported mood
	stress_level – Target variable
==========================================================================================================================================
Environment
Platform: Google Colab
Name: Teen_mental_health_Regression_Model.ipynb
Language: Python
Core Libraries:
	NumPy
	Pandas
	Matplotlib / Seaborn
	Scikit-learn
	SciPy
	Statsmodels
==========================================================================================================================================
Project Workflow

1. Data Loading and Exploration
	Load dataset using Pandas
	Inspect structure (info, describe)
	Check missing and NaN values
2. Outlier Detection and Removal
	Uses Interquartile Range (IQR):
	Q1 (25th percentile)
	Q3 (75th percentile)
	IQR = Q3 − Q1

Outliers defined as:
	Values < Q1 − 1.5 × IQR
	Values > Q3 + 1.5 × IQR
	Rows containing any outlier are removed

3. Data Visualization
	Boxplots for outlier detection
	Scatter plots for feature relationships:
		Screen time vs stress
		Sleep vs stress
		Screen time vs social platforms (with jitter)
==========================================================================================================================================
4. Feature Selection

Input features:

	Screen time
	Social media usage
	TikTok usage
	Sleep hours
	Mood score

Target:

	Stress level
==========================================================================================================================================
5. Train-Test Split
	80% training
	20% testing
	Fixed random seed for reproducibility

6. Model Pipeline

A Scikit-learn pipeline is used:

StandardScaler
	Normalizes feature values
PolynomialFeatures (degree = 3)
	Captures nonlinear relationships
HuberRegressor
	Robust regression model resistant to outliers


7. Model Evaluation
Custom Metrics (implemented from scratch)
	RMSE (Root Mean Squared Error)
	MAE (Mean Absolute Error)
	R² (Coefficient of Determination)
	Adjusted R²

Validation
	Results are verified using Scikit-learn:
		mean_squared_error
		r2_score
==========================================================================================================================================
Key Design Decisions
Robust Regression

	HuberRegressor is used instead of standard linear regression to reduce sensitivity to remaining outliers.

Polynomial Expansion

	Degree 3 polynomial features allow the model to capture complex, nonlinear relationships between digital habits and stress.

Manual Metric Implementation

	Custom metric functions ensure a deeper understanding of model evaluation and correctness through validation against Scikit-learn.
==========================================================================================================================================
How to Run:
	
Open Google Colab
	Upload the ipynb file named: Teen_mental_health_Regression_Model.ipynb
	Upload the dataset from Kaggle
	Place the CSV file in the Colab environment
	Run all cells sequentially

Expected Output
	Cleaned dataset after outlier removal
	Visualizations of feature relationships
	Trained regression model
	Evaluation metrics (Train vs Test):
		RMSE
		MAE
		R²
		Adjusted R²
==========================================================================================================================================

Future Improvements
	Add cross-validation (K-Fold)
	Feature importance analysis
	Try alternative models (Random Forest, Gradient Boosting)
==========================================================================================================================================
License

Dataset licensing and usage terms are defined by the Kaggle dataset provider.