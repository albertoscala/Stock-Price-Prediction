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

With missing data addressed, the subsequent imperative is data normalization, an integral step in preparing our dataset for effective modeling. Employing the MaxMin technique, we scale the data to a standardized range. This technique ensures uniformity and comparability across different features, enhancing the model's ability to converge during training.

The process of data scaling is executed with utmost simplicity. We extract the relevant data `df[features]` and seamlessly integrate it into the scaler through `scaler.fit_transform(df[features])`. This concise yet pivotal step normalizes our dataset, rendering it amenable for optimal model training and subsequent analysis.

### Preparing training

In the context of time series data, the conventional approach to data splitting is no longer arbitrary. Recognizing the inherent temporal dependencies, we adopt a meticulous strategy. Leveraging the `TimeSeriesSplit` function from the `scikit-learn` library, we ensure that our data division into training and test sets maintains the chronological order of observations.

This involves a thoughtful segmentation of the time series data for both the input features and the corresponding expected outputs. By aligning the temporal order, we adhere to a more realistic representation of real-world scenarios, crucial for robust model evaluation and predictive accuracy.

### Building the model

We arrive now to the last part of this project that is actually the most important one: building the model. In this case, we will use a Long Short-Term Memory (LSTM) model, a type of recurrent neural network (RNN) that is particularly well suited to predict time series data.

To the model we add two layers:
- First layer is an LSTM layer with 128 units, with ReLU (Rectified Linear Unit) as activation function.
- Second layer is a Dense layer with 1 unit, with linear activation function. It means that we will only get one output value, which is exactly what we need, since our task was to predict a single future price.

Then to compile the model we use the Adam optimizer, which is a popular choice for neural networks, and the Mean Squared Error (MSE) as loss function, which is also a popular choice when we have regression problems.

Once we are done with the model, we can train it using the `model.fit()` method. We will train it for 100 epochs, with a batch size of 16.

### Prediction

Now to predict the data we simply do `model.predict()`. Then we can plot the predicted data against the actual data to see how well our model performed.

## Conclusions

<p align="center">
  <img src="https://github.com/albertoscala/stock-price-prediction/blob/main/images/graph.png"/>
</p>

A visual inspection of the graph attests to the commendable performance of our model in predicting stock prices. The predicted data aligns remarkably well with the actual data, demonstrating a close correspondence with only minor deviations.

The primary objective of this endeavor was to discern trends that could inform more informed decision-making. The model, in this context, proves adept at capturing and mirroring these trends. Its capacity to closely track actual stock prices substantiates its utility in providing valuable insights for decision support.

In essence, the model effectively fulfills the initial intent of understanding and interpreting trends, laying a solid foundation for enhanced decision-making in the realm of stock market analysis.

## License

[MIT](https://choosealicense.com/licenses/mit/)
