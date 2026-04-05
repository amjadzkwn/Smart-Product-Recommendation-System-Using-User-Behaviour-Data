# Smart Product Recommendation System Using User Behaviour Data

## 🛍️ Smart Product Recommendation System
A personalized recommendation engine built using User Behavior Data (RetailRocket Dataset). This system leverages Collaborative Filtering and Matrix Factorization to predict user interests and suggest relevant products in real-time.

**Dataset Source**: [RetailRocket E-commerce Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Tech Stack](#-tech-stack)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Model Evaluation & Results](#-model-evaluation--results)
- [Installation & Setup](#-installation--setup)
- [Usage Guide](#-usage-guide)
- [Sample Output](#-sample-output)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [License](#-license)

## 🚀 Project Overview
This project focuses on transforming raw e-commerce interaction data (views, add-to-carts, transactions) into an actionable recommendation dashboard. By analyzing past behaviors, the system identifies patterns and predicts the likelihood of a user being interested in items they haven't seen yet.

### Key Objectives:
- Transform raw interaction logs into meaningful user-item interest scores
- Build and optimize a collaborative filtering model using SVD
- Create an interactive Streamlit dashboard for real-time recommendations
- Provide insights into user behavior patterns and product preferences

## 🛠️ Tech Stack
| Component | Technology |
|-----------|------------|
| Language | Python 3.8+ |
| UI Framework | Streamlit |
| Machine Learning | Surprise Library (SVD) |
| Data Processing | Pandas, NumPy |
| Model Persistence | Pickle |
| Visualization | Matplotlib, Seaborn |

## 🧠 Features
- **Real-time Predictions**: Generates top N product recommendations for any Visitor ID instantly
- **User Profile Insights**: Displays interaction history and engagement metrics (total interactions, unique items viewed, interaction distribution)
- **Hybrid Data Integration**: Combines interaction logs with item properties to provide context (category/property) for each recommendation
- **Optimized Performance**: Implements caching (`@st.cache_data` and `@st.cache_resource`) for lightning-fast model loading
- **Interactive Visualizations**: View user interaction patterns, category distributions, and recommendation confidence scores
- **Export Functionality**: Download recommendation results for further analysis

## 📁 Project Structure
Smart-Product-Recommendation-System/
│
├── data/
│ ├── raw/ # Original RetailRocket dataset
│ └── processed/ # Cleaned and transformed data
│
├── notebooks/
│ ├── 01_data_exploration.ipynb
│ ├── 02_data_preprocessing.ipynb
│ └── 03_model_training.ipynb
│
├── src/
│ ├── data_processing.py # Data cleaning and feature engineering
│ ├── model_training.py # SVD model training and evaluation
│ └── utils.py # Helper functions
│
├── app/
│ └── streamlit_app.py # Main dashboard application
│
├── models/
│ └── svd_model.pkl # Trained SVD model
│
├── requirements.txt
├── README.md
└── LICENSE


## 📊 Model Evaluation & Results
To ensure the highest accuracy, the system underwent rigorous testing and optimization:

### 1. Algorithm Comparison (Cross-Validation)
We compared the SVD (Singular Value Decomposition) algorithm against a baseline model (NormalPredictor) to validate its effectiveness:

| Algorithm | RMSE | MAE |
|-----------|------|-----|
| SVD | **2.37** | **1.82** |
| Baseline (Random) | 3.45 | 2.67 |

*SVD significantly outperformed the baseline, showing a ~31% reduction in RMSE.*

### 2. Hyperparameter Tuning
Using Grid Search with 3-fold cross-validation, the model was fine-tuned to find optimal parameters:

**Best Configuration:**
- **RMSE**: 2.3727
- **MAE**: 1.8234
- **Optimal Parameters**:
  - `n_factors`: 100 (number of latent factors)
  - `n_epochs`: 20 (training iterations)
  - `lr_all`: 0.005 (learning rate)
  - `reg_all`: 0.1 (regularization strength)

### 3. Model Performance Metrics
- **Training Time**: ~45 seconds (on standard hardware)
- **Prediction Speed**: <100ms per recommendation
- **Cold-start Handling**: Uses popularity-based fallback for new users

## 🔧 Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip package manager
- Git (optional)

## 💡 Sample Output
Screenshot Streamlit App

![Screenshot Streamlit App](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/58346cfcae3a27143d605b14bab61612dfc150c9/results/UI_example.png)

Recommendations for Visitor ID: 2

![id2](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/345bb6fad4f6b636bed91353dfcfd0e121254e97/results/recommendation_id2.png)

Recommendations for Visitor ID: 17

![Screenshot Streamlit App](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/58346cfcae3a27143d605b14bab61612dfc150c9/results/UI_example.png)

Recommendations for Visitor ID: 64

![Screenshot Streamlit App](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/58346cfcae3a27143d605b14bab61612dfc150c9/results/UI_example.png)

Recommendations for Visitor ID: 1244559

![Screenshot Streamlit App](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/58346cfcae3a27143d605b14bab61612dfc150c9/results/UI_example.png)

🔮 Future Improvements
- Implement Deep Learning models (Neural Collaborative Filtering)
- Add real-time A/B testing framework
- Integrate content-based filtering for cold-start items
- Develop REST API for production deployment
- Add user feedback loop for continuous improvement
- Implement explainable AI features
- Support multi-language interface
- Add recommendation diversity metrics
