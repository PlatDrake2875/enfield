# Energy Consumption Forecasting

## Table of Contents
1. [Project Overview](#project-overview)
2. [Problem Statement](#problem-statement)
3. [Data](#data)
4. [Methodology](#methodology)
5. [Models Implemented](#models-implemented)
6. [Evaluation Metric](#evaluation-metric)
7. [Repository Structure](#repository-structure)
8. [Getting Started](#getting-started)
9. [Results](#results)
10. [Contributing](#contributing)
11. [License](#license)

## 1. Project Overview
This project focuses on forecasting hourly electricity consumption (kWh) for multiple buildings. It leverages historical energy usage data and various weather covariates to build predictive models. The primary goal is to accurately predict future energy needs, which can be crucial for energy management and optimization.

The project encompasses the entire data science pipeline, from data loading and cleaning to exploratory data analysis, feature engineering, model development (including baseline and advanced techniques), and finally, performance evaluation.

## 2. Problem Statement
**Objective:** Forecast hourly electricity consumption (kWh) for multiple buildings.

**Inputs:**
- Historical electricity usage data for individual buildings (time series).
- Weather-related data (e.g., temperature, wind speed) as covariates.

**Key Steps Undertaken:**
1.  Loading, cleaning, and merging of raw data from various sources.
2.  Exploratory Data Analysis (EDA) to understand temporal patterns, seasonality, and the relationship between weather variables and energy load.
3.  Implementation and evaluation of classical baseline forecasting models.
4.  Development and tuning of more advanced models, including sequence-based (GRU - Gated Recurrent Unit) and tree-based (XGBoost) algorithms.
5.  Comparative analysis of model performance using a defined evaluation metric.

## 3. Data
The project utilizes the following datasets:

* **Electricity Consumption Data:** Contains historical hourly electricity usage (kWh) for different buildings.
    * Raw: `unclean.xlsx - Electricity kWh.csv`
    * Cleaned: `clean.xlsx - Electricity kWh.csv`
* **Weather Data:** Includes various meteorological readings (e.g., temperature, humidity, wind speed) corresponding to the timestamps of the consumption data.
    * Raw: `unclean.xlsx - Weather archive.csv`
    * Cleaned: `clean.xlsx - Weather archive.csv`
* **Building Areas Data:** Provides information about the buildings, such as their area, which might be a relevant feature.
    * Raw: `unclean.xlsx - Areas.csv`
    * Cleaned: `clean.xlsx - Areas.csv`

The "unclean" versions represent the raw data as initially provided, while the "clean" versions are the result of preprocessing steps detailed in the `main.ipynb` notebook.

## 4. Methodology
The project follows a structured approach:

1.  **Data Loading and Preprocessing:**
    * Loading the raw CSV files.
    * Handling missing values, data type conversions, and potential outliers.
    * Merging the different data sources (electricity, weather, areas) based on common keys (e.g., timestamps, building identifiers).
2.  **Exploratory Data Analysis (EDA):**
    * Visualizing time series data to identify trends, seasonality (daily, weekly, yearly), and anomalies.
    * Analyzing the correlation between energy consumption and weather variables.
    * Understanding consumption patterns across different buildings.
3.  **Feature Engineering:**
    * Creating time-based features (e.g., hour of day, day of week, month).
    * Generating lag features from historical consumption.
    * Potentially incorporating interaction terms or engineered weather features.
4.  **Model Development:**
    * Splitting data into training and testing sets, ensuring temporal order is maintained.
    * Implementing baseline models to establish a performance benchmark.
    * Developing and training advanced models (GRU, XGBoost).
5.  **Model Evaluation:**
    * Predicting on the test set.
    * Calculating the chosen evaluation metric (MAPE) for each model and each building.
    * Comparing model performance and identifying the best-performing models.

The detailed implementation of these steps can be found in the `main.ipynb` Jupyter Notebook.

## 5. Models Implemented
The project explores a range of forecasting models:

* **Baseline Models:**
    * (Details of specific baseline models like Naive, Seasonal Naive, ARIMA, etc., can be inferred from or added after reviewing the `main.ipynb` notebook's "Baseline Models" section.)
* **Advanced Models:**
    * **GRU (Gated Recurrent Unit):** A type of recurrent neural network (RNN) well-suited for sequence data like time series.
    * **XGBoost (Extreme Gradient Boosting):** A powerful and widely used gradient boosting algorithm, effective for tabular data and capable of capturing complex non-linear relationships.

## 6. Evaluation Metric
The primary metric used to evaluate and compare the performance of the forecasting models is:

* **Mean Absolute Percentage Error (MAPE):**
    $$ \text{MAPE} = \frac{1}{n} \sum_{t=1}^{n} \left| \frac{A_t - F_t}{A_t} \right| \times 100\% $$
    Where $A_t$ is the actual value and $F_t$ is the forecast value at time $t$, and $n$ is the number of observations. MAPE provides an intuitive measure of prediction accuracy as a percentage.

## 7. Repository Structure
.
├── data/
│   ├── raw/
│   │   ├── unclean.xlsx - Electricity kWh.csv
│   │   ├── unclean.xlsx - Weather archive.csv
│   │   └── unclean.xlsx - Areas.csv
│   └── processed/
│       ├── clean.xlsx - Electricity kWh.csv
│       ├── clean.xlsx - Weather archive.csv
│       └── clean.xlsx - Areas.csv
├── notebooks/
│   └── main.ipynb
└── readme.md

## 8. Getting Started

### Prerequisites
* Python 3.x
* Jupyter Notebook or JupyterLab
* Required Python libraries (you can generate a `requirements.txt` file):
    * pandas
    * numpy
    * scikit-learn
    * matplotlib
    * seaborn
    * xgboost
    * tensorflow / keras (for GRU)


### Running the Analysis
1.  Ensure your data files are placed in the correct directories as per the [Repository Structure](#repository-structure).
2.  Open and run the `main.ipynb` notebook using Jupyter Notebook or JupyterLab:
    ```bash
    jupyter notebook notebooks/main.ipynb
    ```
    or
    ```bash
    jupyter lab notebooks/main.ipynb
    ```
    This notebook contains all the steps from data loading and cleaning to model training and evaluation.

## 9. Results
The `main.ipynb` notebook includes a "Results" section where the performance of different models (MAPE scores by building) is presented and visualized. This section provides:
* A comparison of MAPE values across different models and buildings.
* Visualizations of actual vs. predicted values for selected buildings or models.

Please refer to the notebook for detailed findings and discussions.


## 10. License
This project is licensed under the MIT License - see the `LICENSE.md` file for details. (You'll need to create a `LICENSE.md` file with the MIT License text if you choose this license).
