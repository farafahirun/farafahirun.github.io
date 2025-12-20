---
layout: post
title: "AgriForesight: Comparative Study of LSTM & GNN for Rice Price Forecasting"
date: 2025-06-23
author: "Fara Rahmasari Fahirun"
categories: [Data Mining, Machine Learning, Web Development]
tags: [Python, PyTorch, LSTM, GNN, Dashboard, React.js]
image: /assets/img/agriforesight.png
---

## **Project Description**

AgriForesight is a comprehensive data mining project designed to address the high volatility of food commodity prices in Indonesia, specifically focusing on premium rice. Price instability poses significant challenges for the government in formulating strategic policies to ensure economic stability and public welfare.

This research implements a comparative analysis between two advanced Deep Learning architectures: Long Short-Term Memory (LSTM) and Graph Neural Network (GNN). The primary objective is to evaluate the effectiveness of these models in forecasting daily prices using a dataset with limited temporal and spatial features. To make these predictive insights accessible for policy formulation, the project includes the development of an interactive web-based dashboard that visualizes price trends and model performance.

## **Team Contributors**

**A. Tasdik Bijaksana**
As the Project Leader and GNN Specialist, Tasdik led the overall project direction and research methodology. His primary technical responsibility was developing and optimizing the Graph Neural Network architectures, specifically implementing a StemGNN variant for spatial-temporal modeling. He also authored the comprehensive research paper and supervised the team's experimental activities.

**Muh. Naufal Fahri Salim**
Serving as the LSTM Developer and Backend Engineer, Naufal focused on the implementation of the LSTM architecture for time series forecasting. He optimized model performance through rigorous feature engineering and created data preprocessing pipelines. Additionally, he developed the backend API required to integrate the prediction models with the frontend dashboard.

**Fara Rahmasari Fahirun (Me)**
As the Frontend Developer and UI Designer, I was responsible for designing the interactive web dashboard that visualizes the price prediction results. My role involved creating a responsive user interface that allows stakeholders to compare model performance intuitively. I implemented data visualization components to translate complex forecasting data into actionable insights for non-technical users.

**Muh. Aipun Pratama**
Acting as the Research Assistant and Data Analyst, Aipun supported the critical stages of data analysis and research documentation. He assisted in data preprocessing, feature engineering, and experimental validation, ensuring the dataset was clean and structured correctly for model training.

## **Methodology**

### **Dataset**
To ensure the highest level of accuracy and relevance for national policy-making, this research utilized a high-fidelity dataset sourced directly from the **National Food Agency of Indonesia (Badan Pangan Nasional)**. This dataset provides a granular view of daily price fluctuations, serving as the authoritative ground truth for training the Deep Learning models.

* **Source:** [Badan Pangan Nasional RI](https://panelharga.badanpangan.go.id/beranda).
* **Target Commodity:** Premium Rice (Beras Premium).
* **Temporal Coverage:** A comprehensive 3-year time series spanning from **May 2022 to May 2025**, allowing the models to capture seasonal volatility and long-term trends.
* **Scale & Granularity:** The dataset comprises **41,648 data points** distributed across **34 provinces**, providing the necessary spatial density for the Graph Neural Network (GNN) to model inter-provincial price dependencies.
* **Feature Attributes:** The data is structured with key attributes including `Date`, `Province` (Spatial ID), `Commodity Type`, and `Daily Price` (Target Variable).

### **Preprocessing**
For the **LSTM model**, preprocessing involved data cleaning, datetime conversion, and feature engineering. This included adding cyclical time features (sine and cosine of months) and moving averages to help the model capture seasonal trends.

For the **GNN model**, the process was more complex, involving the construction of graphs based on geographical proximity between provinces. The data underwent pivoting, linear interpolation to handle missing values, and normalization using MinMaxScaler.

### **Architecture**
* **LSTM:** A two-layer LSTM network was employed, optimized with a Mean Absolute Error (MAE) loss function to ensure robustness against price outliers.
* **GNN:** A StemGNN variant was implemented to capture both spatial and temporal dependencies simultaneously, utilizing Huber loss for stability.

## **Results and Discussion**

The experimental evaluation on the test set revealed significant performance differences between the two approaches:

| Metric | LSTM (Final) | GNN (Final) | Analysis |
| :--- | :--- | :--- | :--- |
| **MAE** | **319.01** | 451.42 | LSTM error is significantly lower than GNN. |
| **MAPE** | **2.28%** | 3.00% | LSTM demonstrated excellent accuracy with minimal deviation. |
| **RMSE** | **514.80** | 546.93 | LSTM proved more stable in handling variance. |
| **R² Score** | **0.8561** | -5.96 | LSTM fit the data well, while GNN failed to explain the variance. |

**Key Analysis:**
The results demonstrate that the LSTM model is highly effective for short-term forecasting in scenarios with limited features. It successfully captured the sequential dependencies of price trends. In contrast, the GNN model exhibited a negative R² score. This underperformance is attributed to the natural smoothing effect of GNNs, which led to underestimation of sharp price fluctuations. The study suggests that GNNs require richer exogenous features, such as weather or logistics data, to fully leverage their spatial modeling capabilities.

## **Frameworks Used**

* **Data Science & AI:** Python, PyTorch, NumPy, Pandas, Scikit-learn, NetworkX.
* **Frontend Development:** React.js, Tailwind CSS, Chart.js/Recharts.
* **Backend:** Python.

## **Project Links**

* **Research Paper:** [Download Full Paper](https://drive.google.com/file/d/1i-asihzximrA46IB7Jo8gk-RfkcLWJrP/view?usp=sharing)
* **Live Dashboard:** [AgriForesight Dashboard](https://agriforesight.vercel.app/)
* **Frontend Code:** [GitHub Repository](https://github.com/nfahrisalim/AgriForesight.git)
* **Backend Code:** [GitHub Repository](https://github.com/nfahrisalim/AgriForesight_Backend.git)

## **Future Work**

To improve the predictive capabilities, specifically for the GNN model, future research should integrate additional exogenous features such as weather patterns, supply chain logistics, and macroeconomic indicators. Furthermore, exploring hybrid LSTM-GNN architectures could combine the temporal strengths of LSTM with the spatial capabilities of GNN. Expanding the system to include multiple commodities beyond rice would also enhance its utility for food security management.

## **Conclusion**

AgriForesight concludes that for short-term rice price forecasting in Indonesia given limited data features, the LSTM model consistently outperforms the GNN approach. The LSTM model achieved high accuracy and stability, making it a viable candidate for operational early warning systems. The development of the frontend dashboard successfully bridges the gap between complex machine learning research and practical application, providing government stakeholders with a clear, data-driven tool for monitoring price stability.