## 🧠 Welcome to the *Exploring Rainfall Prediction* Notebook!

> Welcome to our Kaggle notebook for the **Exploring Rainfall Prediction** competition! In this notebook, we aim to explore, analyze, and model data from a **Kaggle Competition** to identify factors associated with Rainfall Prediction. This competition is part of Kaggle's **2025 Playground Series 5 Episode 3**, designed to challenge and enhance our machine learning skills. Let’s dive in and uncover insights from the data!

---



<figure>
  <center>
    <img src='https://c4.wallpaperflare.com/wallpaper/231/640/853/walking-in-rain-painting-wallpaper-preview.jpg' 
         height="50px" width="400px" />
  </center>
</figure>

     
# 🏆 Kaggle Competition S5E3: Weather Rainfall Prediction | Logistic Regression 🌦️

## 📋 Table of Contents



### 1. [🎯 Introduction](#🎯-introduction)  
   - Overview of the competition and goals.

### 2. [📦 Libraries and Setup](#📦-libraries-and-setup)  
   - Required libraries and environment setup.

### 3. [🛠️ Data Loading](#🛠️-data-loading-and-initial-analysis)  
   - Data loading, cleaning, and initial exploration.

### 4. [🔧 Feature Engineering](#🔧-feature-engineering)  
   - Extracting meaningful features for prediction.

### 5. [🚂 Model Training](#🚂-model-training-and-evaluation)  
   - Building and training the machine learning models.

### 6. [🎯 Hyperparameter Tuning](#🎯-hyperparameter-tuning-with-optuna)  
   - Optimizing the model using Optuna.

### 7. [📤 Predictions](#📤-saving-predictions)  
   - Generating and saving the predictions.

### 8. [🎉 Conclusion](#🎉-conclusions-and-next-steps)  
   - Final thoughts and next steps.
   
---



## 🎯 Dataset Description for Weather Prediction | Kaggle Competition Data🎯

| Column Name   | Description                                                                 | Data Type |
|----------------|-----------------------------------------------------------------------------|-----------|
| day            | The day number representing the time of the weather data.                    | Integer   |
| pressure       | The atmospheric pressure at the given time, measured in hPa.                | Float     |
| maxtemp        | The maximum temperature for the day in degrees Celsius.                     | Float     |
| temparature    | The average temperature for the day in degrees Celsius.                     | Float     |
| mintemp        | The minimum temperature for the day in degrees Celsius.                     | Float     |
| dewpoint       | The dewpoint temperature in degrees Celsius, indicating moisture in the air.| Float     |
| humidity       | The humidity level in percentage, indicating the amount of moisture in the air.| Float     |
| cloud          | The percentage of cloud cover for the day.                                  | Float     |
| sunshine       | The number of hours of sunshine during the day.                             | Float     |
| winddirection  | The wind direction, measured in degrees from North (0° to 360°).            | Float     |
| windspeed      | The wind speed in km/h.                                                     | Float     |
| rainfall       | The rainfall amount in millimeters for the day (binary classification: 1 for rain, 0 for no rain).| Integer   |

---

**Competition Goal** 🏁  
Predict rainfall occurrence using meteorological data with machine learning.

**Key Challenge** 🔍  
Class imbalance + temporal patterns + hyperparameter in weather data requiring special handling.

**Evaluation Metric** 📏  
**ROC-AUC Score** - Measures model's ability to distinguish between rainy and non-rainy days.

**Our Arsenal** 💡  
- Advanced feature engineering  
- Time-aware cross-validation  
- Hyperparameter optimization with Optuna  
- Logistic Regression as baseline

---

## 🧩 Full Project Architecture


```mermaid
graph TD
    A[Raw Data] --> B[Data Preparation]
    B --> C[Feature Engineering Galaxy]
    C --> D[Preprocessing Pipeline]
    D --> E[Model Training]
    E --> F[Evaluation]
    F --> G[Kaggle Submission]

    %% Data Preparation
    subgraph B[Data Preparation]
        B1[🔄 Merge Train/Test/Extra]
        B2[📅 DateTime Conversion]
        B3[🧹 Handle Missing Values]
        B4[⚖️ Class Balance Check]
    end

    %% Feature Engineering
    subgraph C[Feature Engineering]
        C1[⏳ Temporal Features]
        C2[🌡️ Thermodynamics]
        C3[📈 Rolling Statistics]
        C4[🧩 Polynomial Interactions]
        C5[🌪️ Wind Vector Decomposition]
    end

    %% Preprocessing
    subgraph D[Preprocessing Pipeline]
        D1[🔧 Median Imputation]
        D2[⚖️ Standard Scaling]
        D3[🎯 Feature Selection]
    end

    %% Model Training
    subgraph E[Model Training]
        E1[🎛️ Optuna Tuning]
        E2[🤖 Logistic Regression]
        E3[⏳ TimeSeriesSplit]
        E4[⚖️ Class Weight Handling]
    end

    %% Evaluation
    subgraph F[Evaluation]
        F1[📊 ROC-AUC Curve]
        F2[🎯 Optimal Threshold]
        F3[🤔 Confusion Matrix]
    end

    %% Submission
    subgraph G[Kaggle Submission]
        G1[🔮 Probability Calibration]
        G2[📤 CSV Export]
    end

    %% Styling
    style A fill:#20B2AA,stroke:#333,stroke-width:2px
    style B fill:#87CEEB,stroke:#333,stroke-width:2px
    style C fill:#98FB98,stroke:#333,stroke-width:2px
    style D fill:#FFB6C1,stroke:#333,stroke-width:2px
    style E fill:#DDA0DD,stroke:#333,stroke-width:2px
    style F fill:#FFA07A,stroke:#333,stroke-width:2px
    style G fill:#20B2AA,stroke:#333,stroke-width:2px


