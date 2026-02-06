Ride Price Estimation System (Mini ML Project)
Project Overview
This project implements an end-to-end machine learning system that estimates ride prices based on trip, temporal, demand, and service-related factors.
The goal is not to maximize accuracy, but to demonstrate practical ML thinking: dataset design, feature justification, data quality handling, and model interpretation.
The dataset used in this project is self-designed and synthetic, reflecting how real-world ML projects often begin with imperfect or incomplete data.
Problem Statement
The task is to build a system that estimates the price of a ride using contextual and trip-level information such as distance, duration, demand, traffic, and service type.
The system must:
• Design and justify a custom dataset
• Clean and prepare data for modeling
• Train regression and classification models
• Evaluate and reflect on model behavior and limitations
Why Machine Learning?
Ride pricing depends on multiple interacting factors (distance, time, demand, traffic, weather).
Hard-coded rules struggle to capture these relationships and adapt to new patterns.
Machine learning is better suited because it can:
• Learn non-linear relationships from data
• Adapt to changing conditions
• Generalize pricing behavior from historical examples
The model is expected to learn how temporal, spatial, and demand-driven features jointly influence ride prices.
Dataset Description
• Type: Synthetic, self-created
• Rows: ≥150
• Features: Numerical and categorical
• Target Variable: ride_price (continuous)
The dataset is stored in:
data/rides.csv
Features Used and Justification
Core Identifiers and Target
• key – Unique identifier for each ride (reference only)
• ride_price – Target variable representing the final fare in USD
Temporal Features
• pickup_datetime – Exact pickup time
• time_of_day (morning, afternoon, evening, night)
• pickup_dayofweek (0–6)
Why: Ride demand and pricing vary by hour and day. Peak hours and weekends often lead to higher fares.
Spatial and Trip Geometry
• pickup_longitude, pickup_latitude
• dropoff_longitude, dropoff_latitude
• distance_km
Why: Distance is a primary pricing driver, while location captures congestion, route complexity, and demand hotspots.
Trip Dynamics
• trip_duration_min
• traffic_level (low, medium, high)
Why: Time-based charges and traffic delays directly affect pricing.
Demand and Environment
• demand_level (low, medium, high)
• weather_condition (clear, rainy, snowy, foggy)
Why: High demand and adverse weather often trigger surge pricing or longer trip durations.
Service and Usage Context
• passenger_count
• ride_type (standard, premium)
Why: Different service tiers have different base fares, and passenger count may influence pricing rules.
Feature Considered but Excluded
• Driver rating / vehicle-specific attributes
Excluded because pricing is typically automated and demand-driven, not based on individual driver performance. Including it would add noise without improving prediction quality.
Machine Learning Workflow

1. Data Exploration
   • Inspected dataset structure and statistics
   • Identified missing values, inconsistent labels, and outliers
   • Visualized raw feature distributions
2. Data Cleaning & Feature Engineering
   • Handled missing values
   • Encoded categorical variables
   • Scaled numerical features
   • Detected and treated outliers
   Poor data quality can lead to biased models, unstable predictions, and misleading evaluation results.
3. Regression Model – Ride Price Prediction
   • Model: Linear Regression
   • Train/test split
   • Evaluated using regression metrics
   • Visualized predicted vs actual prices
4. Classification Model – High-Cost vs Low-Cost Rides
   • Created a binary target (high_cost)
   • Model: Logistic Regression
   • Evaluated using:
   o Accuracy
   o Confusion matrix
   • Interpreted probability outputs for decision-making
5. Model Evaluation & Comparison
   • Compared regression and classification behavior
   • Analyzed how data quality affected both models
   • Identified the most influential features driving predictions
   Ethical and Practical Reflection
   • Potential unfair pricing: Surge pricing may disproportionately affect users in high-demand or underserved areas
   • Deployment risk: Over-reliance on synthetic or biased data can lead to unrealistic pricing
   • Dataset limitation: Synthetic data may not fully capture real-world variability and edge cases
   Repository Structure
   ride-price-ml/
   │── data/
   │ └── rides.csv
   │── notebook/
   │ └── ride_price_model.ipynb
   │── README.md
   How to Run
6. Clone the repository
7. Open ride_price_model.ipynb in Google Colab or Jupyter Notebook
8. Run all cells in order
   Key Takeaways
   • Dataset design is as important as model selection
   • Data quality directly impacts model behavior
   • Simple models can still provide meaningful insights when used thoughtfully
