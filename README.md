# Smart Product Recommendation System Using User Behaviour Data

## 🛍️ Smart Product Recommendation System
A personalized recommendation engine built using User Behavior Data (RetailRocket Dataset). This system leverages Collaborative Filtering and Matrix Factorization to predict user interests and suggest relevant products in real-time.

**Dataset Source**: [RetailRocket E-commerce Dataset](https://www.kaggle.com/datasets/retailrocket/ecommerce-dataset)

## 📋 Table of Contents
- [Project Overview](#-project-overview)
- [Features](#-features)
- [Project Structure](#-project-structure)
- [Model Evaluation & Results](#-model-evaluation--results)
- [Sample Output](#-sample-output)
- [Future Improvements](#-future-improvements)

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

## 💡 Sample Output
Screenshot Streamlit App

![Screenshot Streamlit App](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/58346cfcae3a27143d605b14bab61612dfc150c9/results/UI_example.png)

Recommendations for Visitor ID: 2

![id2](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/345bb6fad4f6b636bed91353dfcfd0e121254e97/results/recommendation_id2.png)

Scenario: Active User with High Engagement (User ID: 2)
Description: This user has a clear interaction history (4 items viewed).

Observation: The system utilizes Matrix Factorization to identify latent features from the user's past interests (Interest Scores 1-3).

Result: Recommendations show high Predicted Interest scores (up to 8.11), suggesting the model has high confidence in these items based on the user's specific behavioral patterns.

Recommendations for Visitor ID: 17

![id17](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/a40de3876c3931a800d0ce63364105ace3eaeac0/results/recommendation_id17.png)

Scenario: New User / Cold Start (User ID: 17)
Description: This user has empty interaction history (No previous views or clicks).

Observation: This demonstrates how the system handles the "Cold Start" problem. Since there is no user-specific data, the model defaults to Global Popularity or baseline biases.

Result: Item 40870 appears as the top rank, similar to other users, indicating it is a trending or highly-rated item across the entire platform.

Recommendations for Visitor ID: 64

![id64](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/8df2d4e874ba7ec2cee1c0fc2377d4d933c61b1a/results/recommendation_id64.png)

Scenario: Diverse Interest Profile (User ID: 64)
Description: A user with multiple low-to-medium interest interactions across different items.

Observation: The model balances popular items with specific category-based filtering.

Result: The system suggests items like 306289 and 396064, which possess specific property tags, showing the model's ability to map user interest to complex item attributes.

Recommendations for Visitor ID: 1244559

![id1244559](https://github.com/amjadzkwn/Smart-Product-Recommendation-System-Using-User-Behaviour-Data/blob/5792b9450c2904777e099c85e8d600459b73dede/results/recommendation_id1244559.png)

Scenario: Established User Profile (User ID: 1244559)
Description: A user with a consistent history of multiple interactions.

Observation: The SVD algorithm effectively minimizes the RMSE (Root Mean Square Error) for this user by aligning predicted interest with their historical data.

Result: The system generates a personalized list where items have very close predicted scores (5.34 - 7.66), providing a diversified yet relevant selection of products.

## 🔮 Future Improvements
- Implement Deep Learning models (Neural Collaborative Filtering)
- Add real-time A/B testing framework
- Integrate content-based filtering for cold-start items
- Develop REST API for production deployment
- Add user feedback loop for continuous improvement
- Implement explainable AI features
- Support multi-language interface
- Add recommendation diversity metrics
