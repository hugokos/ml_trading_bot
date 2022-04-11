# ml_trading_bot

This Jupyter Notebook is a machine learning trading bot build on OHLCV data

---

## Technologies

Project uses:

[Pandas](https://pandas.pydata.org/)

[pathlib](https://docs.python.org/3/library/pathlib.html)

[numpy](https://numpy.org/)

[sklearn](https://scikit-learn.org/stable/)

[hvplot](https://hvplot.holoviz.org/)

[matplot](https://matplotlib.org/)

---

## Installation Guide

Run this program in Jupyter notebook and have a Pandas, Pathlib, Numpy, HVPlot, MatplotLib and SKlearn installed. 



---

## Usage

Utilize Jupyter Labs to interact with the software program

!["Jupyter Labs Example"](https://miro.medium.com/max/955/1*mXGu0MeYgnUkyR9ybVlQpg.png)

**Key example code for LogisticRegression model Backtesting**
```
# Use a classification report to evaluate the model using the predictions and testing data
pred_training_report = classification_report(y_train, pred)

# Print the classification report
print(pred_training_report)

# Create a new empty predictions DataFrame.
new_predictions_df = []

# Create a predictions DataFrame
new_predictions_df = pd.DataFrame(index=X_test.index)

# Add the SVM model predictions to the DataFrame
new_predictions_df['Predicted'] = logistic_regression_model.predict(X_test_scaled)

# Add the actual returns to the DataFrame
new_predictions_df['Actual Returns'] = signals_df["Actual Returns"]

# Add the strategy returns to the DataFrame
new_predictions_df['Strategy Returns'] = new_predictions_df["Actual Returns"] * new_predictions_df["Predicted"]

# Review the DataFrame
display(new_predictions_df.head())
display(new_predictions_df.tail())
```

---
## Alternative ML Model Analysis:

Option 1: Tune the training algorithm by adjusting the size of the training dataset. 
Increasing or decreasing the date offset to increase the training data decreased macro avg precision from .82 at 3 months to .74 at 1 month and .64 at 4 months. 

Option 2: Tune the trading algorithm by adjusting the SMA input features. 
Increasing or decreasing the short_window SMA values decreased macro avg accuracy from .82 at 4 to .54 at 10 and .62 at 1. 
Increasing or decreasing the long_window SMA values decreased macro avg accuracy from .82 at 100 to .56 at 75 and .58 at 125.

Option 3: Choose the set of parameters that best improved the trading algorithm returns. 
3 month date offset and 4 short_window and 100 long_window
!['Baseline Model'](./images/original_model.png)


Option 4: Leverage a new machine learning classifier (LogisticRegression)
This logistic regression model preformed worse than the baseline and tuned models. The Logistic Regression model initially had better performance, but ended up under performing in the in the final time periods. 
!['Logistic Regression'](./images/logistic_regression_model.png)

## Contributors

Hugo Kostelni

---

## License

Open Source
'