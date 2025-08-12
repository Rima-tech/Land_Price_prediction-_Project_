# Land Price Valuation using Machine Learning

##📌 Objective
This project builds a robust regression model to predict land plot prices using location, environmental, infrastructure, and socioeconomic factors — enabling real estate developers, planners, investors, and platforms to make faster, data-driven, and transparent decisions.<br>

##📊 Data Overview
The dataset used for this project consists of 1,500 entries and 45 features,each representing various aspects of a land plot. These features include:<br>
•	Geographical attributes such as altitude, slope_deg, soil_quality <br>
•	Location-based infrastructure metrics like distance_to_school_km, distance_to_market_km, proximity_road, and proximity_public_transport <br>
•	Socioeconomic indicators such as median_income_area, GDP_growth_rate, unemployment_rate, and crime_rate <br>
•	Zoning and classification details including land_use, zoning_code, and location_type <br>
•	Environmental risks and characteristics like flood_risk, earthquake_risk, protected_area, and annual_rainfall_mm <br>
•	The target variable: target, which denotes the market price of the land plot. <br>

##🔍 Exploratory Data Analysis (EDA) and Feature Engineering
Comprehensive exploratory data analysis was conducted to understand the nature of the dataset and to guide appropriate preprocessing techniques.<br>
1. Outlier Detection and Handling <br>
Several numerical columns, including annual_rainfall_mm, population_density, employer_density, and hospital_density, showed significant outliers. These outliers were handled using IQR-based capping, ensuring that the extreme values did not distort model learning.<br>
2. Skewness Correction <br>
A number of features exhibited right-skewed distributions, which could adversely affect linear and gradient-based models. To address this, a log transformation (np.log1p) was applied to skewed columns such as distance_city_center_km, annual_rainfall_mm, and school_density.<br>
3. Encoding Categorical Features <br>
Three categorical features — location_type, land_use, and zoning_code — were encoded using pandas' get_dummies(), with drop_first=True to avoid multicollinearity. This enabled the model to process non-numeric inputs effectively without misinterpreting them as ordinal data.<br>
4. Feature Scaling <br>
To ensure that features were on a comparable scale, StandardScaler was applied to all numerical features except for binary variables. This helped the model converge faster and improved its performance in distance-sensitive models.<br>

## Model Training
Several regression models were trained and evaluated to determine the most accurate and generalizable predictor of land price. These included: <br>
•	Linear Regression: A baseline model to establish a reference point. <br>
•	Ridge Regression: A linear model with L2 regularization to mitigate overfitting and multicollinearity. <br>
•	Lasso Regression: A sparse model that can zero out less relevant features using L1 regularization. <br>
•	XGBoost (Base): A tree-based ensemble method known for its speed and performance. <br>
•	XGBoost (Tuned): The same model with optimized hyperparameters via GridSearchCV, improving generalization and fine-tuning learning behavior. <br>
The dataset was split into 80% training and 20% testing, and each model was evaluated using R² Score, MAE, and RMSE on the test set. <br>

##📈 Model Performance Evaluation
The table below summarizes the performance of each model on the test dataset:

<img src="" alt=" model_performance_table" width="900" height="900">

##💼 Business Implication
The results of this project have significant value across multiple areas of the real estate and urban development ecosystem: <br>
🔹 Real Estate Portals and Platforms <br>
By integrating the model into property listing platforms, buyers and sellers can see an estimated land price in real time. This promotes price transparency, reduces negotiation ambiguity, and improves platform credibility.<br>
🔹 Real Estate Developers and Investors <br>
The model helps developers and investors identify undervalued or overpriced plots by comparing predicted vs. listed prices. This data-backed decision support helps in optimizing land acquisition and bidding strategies.<br>
🔹 Urban Planners and Government Agencies <br>
City planners can use the model to simulate how infrastructure changes affect land prices. For example, introducing a new metro line, school, or hospital can be mapped to potential price increases in surrounding areas, allowing better infrastructure ROI estimation. <br>
🔹 Data-Driven Land Valuation <br>
The model identifies the most influential features affecting land price — such as land_area_m2, price_per_m2, location_type, distance_to_market_km, and zoning_code. These insights can be used by appraisers and consultants to explain and justify valuation decisions more transparently to stakeholders. <br>
🔹 Economic Policy and Planning <br>
Since the model incorporates macroeconomic indicators like median_income_area, GDP_growth_rate, and unemployment_rate, it allows policymakers to analyze how broader economic conditions impact land value, informing tax and zoning policy adjustments.<br>







