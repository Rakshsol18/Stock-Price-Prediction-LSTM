# Stock Price Prediction Using LSTM (PyTorch)

A beginner-friendly time-series forecasting project that uses a Long Short-Term Memory (LSTM) neural network built with PyTorch to predict stock closing prices from historical market data.

The notebook compares multiple companies and evaluates the LSTM against a simple persistence baseline.

## Project overview

The notebook downloads historical stock data, prepares chronological training and testing sequences, trains an LSTM model, and compares its predictions with actual closing prices.

### Companies included

- Apple (`AAPL`)
- Microsoft (`MSFT`)
- Alphabet / Google (`GOOG`)

The notebook also allows the date range to be configured.

## Features

- Downloads historical stock data using Yahoo Finance through `yfinance`.
- Compares multiple stock tickers.
- Uses the previous 30 trading days as the input sequence for the next-day prediction.
- Splits data chronologically rather than randomly.
- Fits the feature scaler using training data only to reduce data leakage.
- Builds and trains an LSTM model using PyTorch.
- Evaluates predictions using RMSE, MAE, and MAPE.
- Plots actual versus predicted closing prices.
- Compares the LSTM with a persistence baseline (predicting that the next closing price will equal the latest observed closing price).

## Technologies used

- Python
- Jupyter Notebook
- PyTorch
- NumPy
- pandas
- Matplotlib
- scikit-learn
- yfinance

## Repository contents

```text
Stock-Price-Prediction-LSTM/
├── Stock_Price_Prediction_LSTM.ipynb
├── README.md
└── requirements.txt
```

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/Rakshsol18/Stock-Price-Prediction-LSTM.git
cd Stock-Price-Prediction-LSTM
```

### 2. (Recommended) Create a virtual environment

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Start JupyterLab

```bash
jupyter lab
```

Open `Stock_Price_Prediction_LSTM.ipynb` and run the notebook cells from top to bottom.

## How the model works

1. Historical closing-price data is retrieved for each selected ticker.
2. The data is ordered by date and split into training and testing portions.
3. The scaler is fitted on the training portion only.
4. Sliding windows of 30 previous trading days are created.
5. The LSTM learns patterns in the training sequences.
6. The trained model predicts the next closing price for each test sequence.
7. Predictions are transformed back to the original price scale and evaluated.
8. The LSTM results are compared with the persistence baseline.

## Evaluation

The notebook reports RMSE, MAE, and MAPE for the test period. It also displays actual-versus-predicted plots and a comparison with the persistence baseline.

The metrics describe performance on the selected historical test period. They do not guarantee future performance. Results can vary with the selected date range, data availability, and model settings.

## Data source

Historical stock-market data is retrieved from Yahoo Finance using the `yfinance` Python package. An internet connection is required when the notebook downloads the data.

## Acknowledgement

This project was inspired by the NeuralNine time-series prediction tutorial:

- YouTube: https://www.youtube.com/watch?v=IJ50ew8wi-0
- GitHub tutorial notebook: https://github.com/NeuralNine/youtube-tutorials/blob/main/Time%20Series%20Prediction/Main.ipynb

The project was extended for educational practice with multi-company comparison, evaluation metrics, a persistence baseline, and time-series preprocessing safeguards.

## Limitations

- Stock prices are affected by many factors that are not included in this model.
- The model uses historical price information and cannot account for all market events.
- A good fit on historical data does not mean the model can reliably forecast future prices.
- This is an educational project, not a trading system or investment recommendation.

## License

This repository is intended for educational and portfolio demonstration purposes. Check the licenses and terms of the referenced data source and tutorial before redistributing their material.
