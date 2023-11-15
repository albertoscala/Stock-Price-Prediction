# Stock Price Prediction
This repository, was created with a straightforward objective: to comprehend the mechanics of Long Short-Term Memory (LSTM) models and their practical implementation. Specifically, the focus here is on predicting the adjusted close prices of NVIDIA stocks.

## Installation

To explore and understand the workings of this repository, follow these steps:

1. Clone the repository to your local environment.
2. Review the provided documentation to understand the implementation steps.
3. Create a python virtual enviroment inside the cloned repository using the `python -m venv .` command.
4. Install the requirements using the `bin/pip install -r requirements.txt` command.
5. Dive into the Jupyter notebooks or Python scripts to see the LSTM model in action, particularly in predicting NVIDIA stock prices.

## Implementation

In this section, I will provide a detailed walkthrough of the implementation steps involved in utilizing the LSTM model to predict the adjusted close price of NVDA stocks.

### Understanding the dataset

Embarking on the journey of machine learning necessitates a foundational understanding of the dataset. Within this context, our dataset comprises seven distinct columns, each offering crucial insights:

- **Date**: A straightforward timestamp denoting each data point.
- **Open**: Reflecting the opening price of the stock for a given day.
- **High**: Signifying the peak price reached by the stock on that particular day.
- **Low**: Denoting the lowest recorded price of the stock during the day.
- **Close**: Indicating the closing price of the stock at the end of the trading day.
- **Adjusted Close**: Representing the closing price adjusted for dividends.
- **Volume**: Offering a measure of the total trading activity for the day.

### Preparing the dataset

The initial phase involves meticulous cleaning and addressing inherent issues within the dataset. In this particular instance, all columns are deemed essential for our model, obviating the need for removal. The next critical check involves the identification of `null` values within the dataset using `df.isnull().values.any()`. A `True` return signifies the presence of `null` values, prompting a decision-making juncture.

Confronted with the imperfections in our dataset, two viable options emerge:

- **Removal of Rows**: Eliminating rows containing null values.
- **Mean Replacement**: Substituting null values with the mean of the respective column.

Opting for data continuity, I chose the latter approach, executing `df.fillna(df.mean(), inplace=True)`. Subsequently, a reevaluation via the null value check `df.isnull().values.any()` confirms the successful mitigation of the issue, with a `False` return indicating the absence of null values in the dataset. This strategic choice ensures the preservation of data integrity while fostering a more seamless dataset for subsequent phases.

### Preparing training

### Building the model

### Prediction and analysis

## License

[MIT](https://choosealicense.com/licenses/mit/)
