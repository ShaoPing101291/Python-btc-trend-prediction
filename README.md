# Python-btc-trend-prediction
Predict if Bitcoin will go up in the next 10 days using machine learning and technical indicators.

This project uses machine learning to predict whether Bitcoin (BTC) will rise in the next 10 days based on technical analysis indicators.  
I use `yfinance` for data collection, `ta` for feature engineering, and `RandomForestClassifier` for model training.

---

# 1. Preparing the Dataset

First, I collect 5 years of daily BTC-USD price data using `yfinance`.  
Then, I calculate technical indicators like RSI, MACD, EMA, SMA, OBV, ATR, and Bollinger Bands using the `ta` library.  
I also create a label called `label_10d_up`, which is `1` if the price goes up after 10 days, otherwise `0`.  
This labeled dataset will be used to train our machine learning model.

➡️ Output: `BTC_Technical_Indicators_with_Label.xlsx`

---

# 2. Model Training with Random Forest

I use a `RandomForestClassifier` to learn patterns from the technical indicators.  
I split the data into training and test sets and train the model.

✅ The best model achieves around **85% accuracy** on test data.

➡️ Output: `BTC_model.pkl`

---

# 3. Hyperparameter Tuning

I fine-tune the model using `GridSearchCV` and `RandomizedSearchCV` to find the best parameters such as:

- `n_estimators` (number of trees)
- `max_depth` (tree depth)
- `min_samples_leaf`, `max_features`
- `bootstrap` method

- `GridSearchCV`: tests all combinations (more thorough but slower)
- `RandomizedSearchCV`: tests random combinations (faster for large grids)

---

# 4. Visualizing the Model

I visualize a single decision tree from the forest using `plot_tree()`  
and also plot the feature importance chart.

➡️ Output: `feature_importance.png`

---

# 5. Predicting with New Data

I download the latest 3 months of BTC data, calculate technical indicators, and use the trained model to predict if BTC will go up in the next 10 days.

Example output:
`Prediction: BTC may go up in the next 10 days (probability: 72.4%)`
`Suggestion: Consider buying in`


# Acknowledgements

This was supported by **telunyang**.

I also referenced the following open-source resources during development:

- [telunyang/python_machine_learning](https://github.com/telunyang/python_machine_learning) 
- [TA-Lib documentation](https://technical-analysis-library-in-python.readthedocs.io/)
- [Scikit-learn official docs](https://scikit-learn.org)
- [yFinance API](https://pypi.org/project/yfinance/)
