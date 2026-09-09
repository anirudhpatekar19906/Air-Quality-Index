# 🌍 Air Quality Forecasting Using LSTM

## 📌 Project Description

This project develops a **time-series forecasting system using a Long
Short-Term Memory (LSTM) network** to predict **Carbon Monoxide (CO(GT))
concentration** using historical observations from the **UCI Air Quality
Dataset**.

The project includes data preprocessing, chronological splitting,
normalization, 24-hour sequence preparation, LSTM model training,
testing, and regression-based performance evaluation.

------------------------------------------------------------------------

## 📊 Dataset Information

-   **Dataset:** Air Quality Dataset
-   **Source:** UCI Machine Learning Repository
-   **Dataset ID:** 360
-   **Application Area:** Air Quality Monitoring and Environmental
    Forecasting
-   **Target Variable:** `CO(GT)`

### 🔑 Important Attributes

-   `Date`, `Time` -- Date and time of observation
-   `CO(GT)` -- Carbon Monoxide concentration (target)
-   `NMHC(GT)` -- Non-Methane Hydrocarbons concentration
-   `C6H6(GT)` -- Benzene concentration
-   `NOx(GT)` -- Nitrogen Oxides concentration
-   `NO2(GT)` -- Nitrogen Dioxide concentration
-   `PT08.S1(CO)` to `PT08.S5(O3)` -- Gas sensor measurements
-   `T` -- Temperature
-   `RH` -- Relative Humidity
-   `AH` -- Absolute Humidity

------------------------------------------------------------------------

## 🎯 Project Objective

The objective is to use the **previous 24 hours of air quality
observations** to predict the **next hour's CO(GT) concentration** using
an LSTM model.

------------------------------------------------------------------------

## 🛠️ Technologies Used

-   🐍 Python
-   🔢 NumPy
-   🐼 Pandas
-   📈 Matplotlib
-   📚 UCI ML Repository (`ucimlrepo`)
-   🤖 Scikit-learn
-   🧠 TensorFlow / Keras
-   ☁️ Google Colab

------------------------------------------------------------------------

## 📥 Dataset Loading

``` python
!pip install ucimlrepo

from ucimlrepo import fetch_ucirepo
import pandas as pd

air_quality = fetch_ucirepo(id=360)
df = pd.DataFrame(air_quality.data.features)
```

------------------------------------------------------------------------

# 🔄 Project Workflow

## 1️⃣ Dataset Understanding

The dataset was examined for its structure, attributes, data types,
missing values, and basic statistics.

## 2️⃣ Data Pre-processing

The following preprocessing operations were performed:

-   🔄 Replaced `-200` values with `NaN`
-   🧹 Handled missing values using interpolation and forward/backward
    filling
-   🔍 Checked and removed duplicate records where required
-   📅 Standardized `Date` and `Time`
-   🕒 Created a `DateTime` column
-   ⏳ Sorted the data chronologically
-   🎯 Selected input features and target variable
-   📏 Applied Min-Max normalization

## 3️⃣ Input and Target Variables

**🎯 Target Variable:**

``` text
CO(GT)
```

**📥 Input Features:** 13 air quality and environmental measurements.

## 4️⃣ Training, Validation and Testing Split

The dataset was split chronologically into:

-   🟢 **70% Training**
-   🟡 **10% Validation**
-   🔵 **20% Testing**

Random shuffling was not performed, and testing data was not used during
model training.

## 5️⃣ Data Normalization

📏 Min-Max Scaling was applied using separate scalers for input features
and the target variable. The scalers were fitted only on training data
to prevent data leakage.

## 6️⃣ Time-Series Sequence Preparation

A **24-hour time window** was used. The previous 24 observations are
used to predict the next `CO(GT)` value.

**📥 Input Shape:**

``` text
(samples, 24, 13)
```

**📤 Output Shape:**

``` text
(samples, 1)
```

------------------------------------------------------------------------

# 🧠 LSTM Model Architecture

The model contains:

1.  🧠 LSTM layer with **64 units**
2.  💧 Dropout layer with **0.2 rate**
3.  🧠 LSTM layer with **32 units**
4.  💧 Dropout layer with **0.2 rate**
5.  🎯 Dense output layer with **1 neuron**

### ⚙️ Model Configuration

-   **Model:** LSTM
-   **Input Features:** 13
-   **Time Steps:** 24
-   **LSTM Units:** 64 and 32
-   **Output Layer:** 1 neuron
-   **Loss Function:** Mean Squared Error (MSE)
-   **Optimizer:** Adam
-   **Epochs:** 50
-   **Batch Size:** 32
-   **Early Stopping:** Enabled

------------------------------------------------------------------------

## 🚀 Model Training

The model was trained using training data and monitored using validation
data. Early stopping was used to reduce overfitting.

------------------------------------------------------------------------

## 📏 Model Evaluation

The trained model was evaluated on unseen testing data.

The following metrics were calculated:

-   📉 **MAE** -- Mean Absolute Error
-   📉 **MSE** -- Mean Squared Error
-   📉 **RMSE** -- Root Mean Squared Error
-   📊 **R² Score** -- Coefficient of Determination

Predictions were inverse-transformed before evaluation.

------------------------------------------------------------------------

## 📈 Visualizations

The project includes:

-   📈 CO(GT) concentration over time
-   📉 Training and validation loss
-   🔄 Actual vs Predicted CO(GT) values

------------------------------------------------------------------------

## 📁 Project Structure

``` text
Air-Quality-Index/
│
├── 📓 DL_CA1_Project.ipynb
└── 📄 README.md
```

------------------------------------------------------------------------

## ▶️ How to Run

1.  ☁️ Open the notebook in **Google Colab**.
2.  📦 Install the required packages.
3.  ▶️ Run the cells sequentially.
4.  📥 The dataset is loaded directly from the UCI Machine Learning
    Repository.
5.  🧠 Train the LSTM model and view the evaluation results.

------------------------------------------------------------------------

## 📝 Conclusion

This project demonstrates the use of an **LSTM deep learning model for
multivariate time-series forecasting**. Historical air quality
observations are used to predict future Carbon Monoxide concentrations,
demonstrating an application of deep learning in environmental
monitoring and air quality forecasting.

------------------------------------------------------------------------

## 👨‍💻 Author

**Anirudh Patekar**
