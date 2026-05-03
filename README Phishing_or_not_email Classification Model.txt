README Phishing_or_not_email Classification Model

Overview

Phishing_or_not_email_Classification_Model is a machine learning project built in Google Colab to classify emails as safe or phishing.

The model combines:

	Natural Language Processing (TF-IDF)
	Manually engineered phishing indicators
	Ensemble learning (Random Forest with hyperparameter tuning)

This hybrid approach improves detection by capturing both statistical language patterns and explicit phishing signals.
=========================================================================================================================================
Dataset

Source: Phishing Emails Dataset
Platform: Kaggle

Download required:
The dataset is too large for GitHub and must be downloaded manually:
https://www.kaggle.com/datasets/subhajournal/phishingemails

File name: Phishing_Email.csv
=========================================================================================================================================

Environment
	Platform: Google Colab
	Language: Python
Core Libraries
	NumPy, Pandas
	Matplotlib, Seaborn
	Scikit-learn
	SciPy
	XGBoost
	Regex (re)
=========================================================================================================================================

Project Workflow
1. Data Loading and Inspection
	Load dataset using Pandas
	Inspect:
		head() → sample data
		info() → structure
		describe() → statistics
	Identify class labels (Safe Email, Phishing Email)

2. Data Preprocessing
	Label Encoding
		Safe Email → 0  
		Phishing Email → 1
	Text Cleaning
		Handle missing values
		Convert all text to lowercase
		Ensure all entries are valid strings
=========================================================================================================================================

3. Manual Feature Engineering

Custom phishing indicators are extracted from each email:

	Number of links (http/https)
	Number of exclamation marks
	Count of uppercase words
	Presence of urgency keywords:
	“urgent”, “act now”, “verify now”
	Presence of financial keywords:
	“bank”, “payment”, “invoice”
	Email length

These features capture behavioral patterns typical of phishing attacks.
=========================================================================================================================================

4. Text Vectorization (TF-IDF)

Uses:

	TfidfVectorizer

Configuration:

	Stop words removed (English)
	Max features: 10,000
	N-grams: 1 to 3 words

Purpose:
	Convert text into numerical form while emphasizing words that are important for classification.
=========================================================================================================================================

5. Feature Combination

Two feature sets are merged:

	TF-IDF features (text patterns)
	Manual features (phishing signals)
	X_final = hstack([X_text, X_manual])

This creates a high-dimensional, information-rich feature space.
=========================================================================================================================================

6. Train-Test Split
	80% training
	20% testing
	Stratified split to preserve class balance
7. Model Selection and Training

Model used:

	RandomForestClassifier
	Hyperparameter Tuning
=========================================================================================================================================

Uses:

	RandomizedSearchCV

Parameters explored:

	n_estimators: [100, 200]
	max_depth: [None, 10]

Why Random Forest:

	Handles high-dimensional data well
	Resistant to overfitting with proper tuning
	Works effectively with mixed feature types
=========================================================================================================================================

8. Model Evaluation
Metrics:
	Accuracy
	F1 Score
	Confusion Matrix
	Classification Report
Visualization:
	Confusion matrix plotted using:
	ConfusionMatrixDisplay
=========================================================================================================================================
How to Run
	Open Google Colab
	Download dataset from Kaggle
	Upload Phishing_Email.csv into Colab
	Run all cells sequentially
=========================================================================================================================================

Expected Output
	Cleaned and processed dataset
	Extracted feature matrix
	Trained classification model
	Best hyperparameters from search
	Confusion matrix visualization
	Classification report with precision, recall, F1-score
=========================================================================================================================================

Key Design Decisions
Hybrid Feature Strategy

Combines:

	TF-IDF → captures language patterns
	Manual features → captures known phishing signals

This improves detection accuracy compared to using only one method.

RandomizedSearchCV

Used instead of GridSearch to:

	Reduce computation time
	Efficiently explore parameter space

Stratified Sampling

Ensures both classes are proportionally represented in train/test sets.
=========================================================================================================================================

Limitations
	Limited hyperparameter search space
	No deep learning or transformer-based models
	Manual keyword list may miss evolving phishing tactics
	Model performance depends on dataset quality

Future Improvements
	Expand hyperparameter tuning
	Try advanced models:
		Gradient Boosting
		XGBoost
	Transformer-based NLP models (e.g., BERT)
	Add more phishing keyword patterns
	Deploy as a real-time email filter API
	Perform cross-validation for more robust evaluation
=========================================================================================================================================

License

Dataset usage and licensing are defined by the Kaggle dataset provider.