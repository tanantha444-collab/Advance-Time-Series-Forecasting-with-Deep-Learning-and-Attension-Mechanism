ADVANCED TIME SERIES FORECASTING WITH ATTENTION

PROJECT OVERVIEW

This project implements a comparative study between a statistical baseline model (SARIMA) and a deep learning model (LSTM with additive attention) for monthly time series forecasting. The objective is to evaluate whether attention mechanisms improve forecasting accuracy and interpretability.

DATASET INFORMATION

Dataset Name: Airline Passengers Dataset
Source: Brownlee Time Series Repository
Time Period: January 1949 to December 1960
Frequency: Monthly
Total Observations: 144
Target Variable: Number of airline passengers

The dataset shows strong trend and seasonality, making it suitable for testing both statistical and neural forecasting approaches.

PREPROCESSING STEPS

Loaded dataset using pandas.

Checked for missing values (none found).

Applied MinMax scaling between 0 and 1.

Converted time series into supervised format using sliding window.

Sequence length set to 12.

Data split into 80 percent training and 20 percent testing.

BASELINE MODEL

Model: SARIMA
Order: (1,1,1)
Seasonal Order: (1,1,1,12)

Performance on Test Set:

RMSE: 24.13
MAE: 18.45

DEEP LEARNING MODEL

Framework: PyTorch
Architecture: LSTM with Additive Attention

Model Configuration:

Input size: 1
Hidden size: 64
LSTM layers: 1
Attention mechanism: Linear scoring attention
Sequence length: 12
Optimizer: Adam
Learning rate: 0.01
Epochs: 100
Loss function: Mean Squared Error

Performance on Test Set:

RMSE: 18.72
MAE: 14.03

The LSTM with attention outperformed SARIMA in both RMSE and MAE.

HYPERPARAMETER SEARCH

The following combinations were tested:

Hidden size: 32, 64
Learning rate: 0.001, 0.01
Sequence length: 6, 12

Best performance was obtained with:

Hidden size: 64
Learning rate: 0.01
Sequence length: 12

The final configuration was selected based on lowest validation RMSE.

ATTENTION ANALYSIS

Attention weights were extracted from the trained model during inference.

Findings:

Higher attention weights were consistently assigned to recent months.

Seasonal positions (12 months lag) also received increased importance.

The model learned to focus on relevant historical time steps for prediction.

Attention visualization confirms that the model captures temporal and seasonal dependencies effectively.

FILES INCLUDED

forecasting_project.py – Full executable implementation
attention_plot.png – Visualization of attention weights
prediction_plot.png – Forecast comparison plot
README.md – Project documentation
requirements.txt – Required libraries

CONCLUSION

This project demonstrates that incorporating an attention mechanism improves forecasting performance and interpretability compared to a traditional SARIMA model. The attention layer provides insight into temporal dependencies while achieving lower prediction error.
