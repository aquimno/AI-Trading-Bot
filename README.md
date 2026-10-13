# AI Trading Bot

An experimental machine learning trading bot developed for my **Introduction to Artificial Intelligence (CAP 4630)** course.

The project uses market data from the **OANDA API** and a **Logistic Regression** model to predict whether the next 5-minute EUR/USD candle will move up or down. The model uses technical indicators and price-based features to identify patterns in short-term market movements.

## Project Goal

The goal of this project was to explore how machine learning can be applied to financial market data and evaluate whether technical indicators can help predict short-term price direction.

The model treats the problem as a binary classification task:

* `1` → Next candle closes higher
* `0` → Next candle does not close higher

## Data

Market data is retrieved from the **OANDA API** using a demo account.

* **Instrument:** EUR/USD
* **Timeframe:** 5-minute candles (M5)
* **Data:** Open, High, Low, and Close prices
* **Dataset size:** Up to 1,000 candles retrieved from OANDA

## Technical Indicators & Features

The model uses 16 features based on trend, momentum, volatility, and price structure.

### Trend

* EMA 5
* EMA 8
* EMA 20
* EMA Trend

### Momentum

* Price Return
* 3-period Momentum
* 5-period Momentum

### Volatility

* 10-period Volatility
* 20-period Volatility
* ATR 14

### Other Indicators

* RSI 14
* Bollinger Band Position
* 10-period Breakout Up
* 10-period Breakout Down
* Price vs. EMA 8

These features are calculated from the market data before being passed to the machine learning model.

## Machine Learning Model

### Logistic Regression

The project uses **Logistic Regression** as the primary classification model.

The dataset is divided into:

* **80% training data**
* **20% testing data**

The data is not shuffled when splitting the training and testing sets so that the model is evaluated on later observations rather than randomly mixed historical observations.

## Evaluation

The model is evaluated using:

* Classification accuracy
* Training accuracy
* Testing accuracy
* Trading win rate
* Total strategy return
* Number of trades
* Equity curve

The project also generates an equity curve to visualize how the simulated strategy performs over the testing period.

## Results

The model's predictive accuracy was relatively limited, reaching approximately **60% or less** depending on the dataset and run.

This demonstrates one of the major challenges of applying machine learning to short-term financial markets: market movements contain a significant amount of noise and are difficult to predict consistently using a limited set of technical indicators.

Rather than treating accuracy as the only measure of success, this project also evaluates the model through simulated trading performance and an equity curve.

## Limitations

There are several limitations to the current implementation:

* The model uses a relatively small dataset.
* The prediction timeframe is only 5 minutes.
* Financial markets are highly noisy and unpredictable.
* The model currently uses a limited number of market-derived features.
* Transaction costs and spreads are not fully incorporated into the strategy evaluation.
* The project has not been demonstrated to produce consistent real-world profits.
* The model is trained and evaluated on historical data and should not be assumed to perform similarly in live markets.

## Future Improvements

Possible improvements include:

* Using a larger historical dataset
* Testing additional machine learning models
* Hyperparameter tuning
* Adding additional technical indicators
* Testing different timeframes
* Improving feature engineering
* Adding transaction costs and spread to the backtest
* Performing more comprehensive backtesting
* Comparing the model against baseline trading strategies
* Evaluating additional metrics such as precision, recall, F1-score, and ROC-AUC
* Testing the model on unseen market periods

## Disclaimer

This project was created for **educational purposes** as part of an Introduction to Artificial Intelligence course.

It is **not financial advice** and is not intended to recommend or execute real-money trades. The model has limited predictive accuracy, and past or simulated performance does not guarantee future results.

## Author

**Ana Quimno**

University of North Florida
Computer Science
