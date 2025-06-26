---
layout: post
date: 2025-06-23
author: "Fara Rahmasari Fahirun"
title: "AgriForesight: Rice Price Forecasting with LSTM and GNN Models"
categories: [Data Mining, Machine Learning, Deep Learning, Time Series]
description: A comparative study of GNN and LSTM for multivariate forecasting of premium rice prices across Indonesian provinces using limited temporal and spatial features with interactive dashboard.
tags: [Python, PyTorch, LSTM, GNN, Time Series Forecasting, Data Mining, Agriculture]
image: /assets/img/agriforesight.png
---

# **AgriForesight**

A comprehensive data mining project that implements and compares Long Short-Term Memory (LSTM) and Graph Neural Network (GNN) models for predicting premium rice prices across Indonesian provinces. This research addresses the critical need for accurate food price forecasting to support government policy formulation and economic stability.

> **Research Focus:** Comparative analysis of deep learning models for agricultural price prediction using limited temporal and spatial features.

**Live Dashboard:** [View AgriForesight Dashboard](https://agriforesight.vercel.app/)  
**Research Paper:** [Download Full Paper](/assets/docs/Paper%20Data%20Mining%20Kelompok%207.pdf)

## **Research Team Collaboration**

This project was developed through collaborative effort by a dedicated team of four researchers, each contributing specialized expertise in different aspects of machine learning and data analysis.

**1. A. Tasdik Bijaksana** - *Project Leader & GNN Specialist*
- **Primary Responsibilities:** Project leadership, GNN model development, and research paper writing
- **Key Contributions:**
  • Led overall project direction and research methodology
  • Developed and optimized Graph Neural Network architectures
  • Implemented StemGNN variant for spatial-temporal modeling
  • Authored comprehensive research paper and literature review
  • Supervised and coordinated all team activities

**2. Muh. Naufal Fahri Salim** - *LSTM Developer & Backend Engineer*
- **Primary Responsibilities:** LSTM model implementation and dashboard backend development
- **Key Contributions:**
  • Designed and implemented LSTM architecture for time series forecasting
  • Developed backend API for dashboard integration
  • Optimized model performance through feature engineering
  • Created data preprocessing pipelines for temporal analysis

**3. Fara Rahmasari Fahirun** - *Frontend Developer & UI Designer*
- **Primary Responsibilities:** Dashboard frontend design and user interface development
- **Key Contributions:**
  • Designed interactive web dashboard for price prediction visualization
  • Created responsive user interface for model comparison
  • Implemented data visualization components for forecasting results
  • Developed user-friendly interface for accessing prediction models

**4. Muh. Aipun Pratama** - *Research Assistant & Data Analyst*
- **Primary Responsibilities:** Supporting data analysis and research documentation
- **Key Contributions:**
  • Assisted in data preprocessing and feature engineering
  • Supported model evaluation and performance analysis
  • Contributed to research methodology documentation
  • Helped with experimental validation and testing

**Institution:** Hasanuddin University, Indonesia  
**Course:** Data Mining

## **Project Overview**

AgriForesight addresses the challenge of volatile food commodity prices in Indonesia, which pose significant difficulties for accurate prediction and policy formulation. The project focuses on premium rice price forecasting using advanced deep learning techniques to enable proactive government intervention.

**Research Objectives**
• Compare LSTM and GNN performance on Indonesian rice price data
• Develop accurate predictions using limited temporal and spatial features
• Provide policy recommendations for government food price management
• Create accessible dashboard for stakeholder decision-making

## **Methodology & Technical Approach**

#### **Data Collection & Preprocessing**

The research utilized a comprehensive dataset containing 41,648 rows of rice price data spanning from May 2022 to May 2025, scraped from the official government website (panelharga.badanpangan.go.id).

**Dataset Characteristics**
• **Coverage:** Premium rice prices across Indonesian provinces
• **Temporal Range:** 3-year period with daily observations
• **Features:** Date, commodity type, province, and price information
• **Size:** 41,648 data points across multiple provinces

#### **Model Implementation**

**LSTM Architecture**
• Two-layer LSTM network optimized for sequential time series modeling
• Feature engineering including cyclical time features and moving averages
• MAE loss function for robust training against outliers
• 30-day input sequences for 30-day prediction horizon

**GNN Architecture**
• StemGNN variant incorporating spectral graph convolution
• Graph construction based on geographical proximity between provinces
• Spatial-temporal modeling capturing both geographic and temporal dependencies
• Huber loss function for robustness to price volatility

**Feature Engineering**
• Temporal features: month sine/cosine encoding, moving averages
• Spatial features: province proximity mapping for graph construction
• Volatility indicators and seasonality encoding
• MinMaxScaler normalization applied per province

## **Key Research Findings**

#### **Performance Comparison**

The experimental evaluation revealed significant performance differences between the two approaches:

**LSTM Model Results**
• **MAE:** 319.01 (significantly improved from initial 740.07)
• **MAPE:** 2.28% (excellent accuracy for price prediction)
• **RMSE:** 514.80 (substantial improvement through optimization)
• **R² Score:** 0.8561 (strong explanatory power)

**GNN Model Results**
• **MAE:** 451.42 (moderate performance with room for improvement)
• **MAPE:** 3.00% (acceptable but higher than LSTM)
• **RMSE:** 546.93 (comparable to LSTM but less stable)
• **R² Score:** -5.9673 (indicates need for architectural refinement)

#### **Key Insights**

**LSTM Advantages**
• Excelled at capturing sequential temporal dependencies
• Highly effective with limited but relevant temporal features
• Consistent performance across different prediction horizons
• Better suited for short-term price forecasting scenarios

**GNN Challenges**
• Natural smoothing effect led to under/over-estimation in some cases
• Required richer exogenous features for optimal performance
• Spatial modeling power underutilized due to limited spatial features
• Showed potential but needed additional weather and economic data

## **Dashboard Development**

#### **Frontend Architecture**

My primary contribution focused on creating an intuitive, responsive dashboard that makes complex machine learning predictions accessible to stakeholders.

**User Interface Design**
• Clean, professional layout optimizing data visualization clarity
• Interactive charts displaying actual vs predicted price trends
• Model comparison interface allowing real-time performance evaluation
• Responsive design ensuring accessibility across different devices

**Visualization Components**
• Time series plots showing prediction accuracy over time
• Province-wise comparison charts for spatial analysis
• Performance metrics dashboard with key evaluation indicators
• Interactive filtering options for different time periods and regions

**Technical Implementation**
• Modern web technologies ensuring fast loading and smooth interactions
• Integration with backend API for real-time model predictions
• Optimized data presentation for both technical and non-technical users
• Mobile-responsive design for stakeholder accessibility

## **Research Impact & Applications**

#### **Policy Implications**

The research provides valuable insights for government food security management:

**Early Warning Systems**
• LSTM models suitable for developing operational price monitoring systems
• Accurate short-term forecasts enabling proactive policy intervention
• Dashboard interface facilitating real-time decision-making for stakeholders

**Strategic Planning**
• Price trend analysis supporting resource allocation decisions
• Market stability assessment through predictive modeling
• Evidence-based policy formulation using data-driven insights

#### **Technical Contributions**

**Machine Learning Advances**
• Demonstrated LSTM effectiveness for agricultural price prediction with limited features
• Identified GNN improvement opportunities through feature enrichment
• Established baseline performance metrics for Indonesian rice price forecasting

**Practical Applications**
• Interactive dashboard bridging gap between research and practical implementation
• Scalable architecture supporting extension to other commodities
• User-friendly interface enabling non-technical stakeholder adoption

## **Future Enhancements**

**Model Improvements**
• Integration of weather data and macroeconomic indicators for GNN enhancement
• Hybrid LSTM-GNN architectures combining temporal and spatial strengths
• Advanced feature engineering incorporating supply chain and policy variables
• Extended evaluation across multiple agricultural commodities

**Dashboard Expansion**
• Real-time data integration for live price monitoring
• Advanced analytics features including trend analysis and anomaly detection
• Multi-commodity support expanding beyond rice to other staple foods
• Mobile application development for broader stakeholder access

**Research Extensions**
• Cross-regional validation testing model generalizability
• Integration with existing government information systems
• Development of automated alert systems for price volatility detection
• Collaboration with agricultural economists for enhanced policy recommendations

---

> **Personal Reflection:** Leading the frontend development for AgriForesight allowed me to bridge the gap between complex machine learning research and practical stakeholder needs. Creating an intuitive dashboard that makes sophisticated price prediction models accessible to government officials and policy makers was both challenging and rewarding. This project reinforced my passion for using technology to solve real-world problems in agriculture and food security.

> **Team Achievement:** AgriForesight demonstrates the power of interdisciplinary collaboration, combining machine learning expertise, backend development, and user interface design to create a comprehensive solution for agricultural price forecasting. Our diverse skill sets enabled us to develop both cutting-edge predictive models and practical tools for implementation.

**Repositories:**  
**Frontend:** [View on GitHub](https://github.com/nfahrisalim/AgriForesight.git)  
**Backend:** [View on GitHub](https://github.com/nfahrisalim/AgriForesight_Backend.git)

**Live Dashboard:** [AgriForesight Platform](https://agriforesight.vercel.app/)

---

*Interested in agricultural technology, data mining, or machine learning applications? Feel free to reach out to discuss research collaboration opportunities!*