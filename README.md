# Analysis of Miami Housing Dataset


## Problem Statement

Over the last decade, the cost of housing in the United States has escalated significantly, making homeownership a challenging goal for many Americans. This rising trend is particularly evident in Miami, one of the fastest-growing real estate markets in the country, where the increase in home prices has been remarkable. The pressing need to understand the underlying factors contributing to these price increases is crucial. This project aims to dissect and analyze the key elements influencing housing costs in Miami. By pinpointing these drivers, the study seeks to provide crucial insights that will aid potential buyers and sellers in making well-informed decisions. Additionally, the findings will assist policymakers in developing strategies to enhance housing affordability. The analysis will also explore which neighborhoods offer more economically feasible options, thus guiding buyers in making cost-effective housing choices within their budgets.


### Steps followed 
Step 1: Load the Miami Housing Dataset from Kaggle containing various attributes affecting housing prices.

Step 2: Perform initial data preparation, filtering and normalizing key variables like SALE_PRC.

Step 3: Use scatter plots and data statistics to visualize and understand variable distributions and relationships.

Step 4: Conduct correlation analysis to identify significant relationships between variables and sale prices.

Step 5: Develop a basic regression model to understand how various factors impact housing prices.

Step 6: Introduce interaction terms between variables like OCEAN_DIST and WATER_DIST to enhance model accuracy.

Step 7: Construct a third order model to refine predictions, incorporating model diagnostics like QQ plots.

Step 8: Analyze residuals to identify patterns and deviations suggesting potential model issues.

Step 9: Evaluate the effectiveness of models using adjusted R-squared values to select the optimal model.

Step 10: Draw conclusions on the influence of location-based and other factors on housing prices.

Step 11: Document findings and methodologies in a structured report, highlighting key insights and recommendations.

### Variables
In the Miami housing dataset analysis, the data was categorized into three main areas for focused study. Location-based factors—like proximity to amenities and highways—assessed how geography affects housing prices. Structural attributes—such as property size and building age—explored the physical characteristics influencing prices. Lastly, a comprehensive approach combined these elements to develop an integrated model that captures the complex factors determining housing prices in Miami. This categorization helped streamline the analysis, enhancing the clarity and effectiveness of the insights.

(a) SALE_PRC: Sale price of the property (in USD).

(b) LND_SQFOOT: Land area (in square feet).

(c) TOT_LVG_AREA: Total living area (in square feet).

(d) SPEC_FEAT_VAL: Monetary value of special features like swimming pools (in USD).

(e) RAIL_DIST: Distance to the nearest rail line (feet) - an indicator of noise.

(f) OCEAN_DIST: Proximity to the ocean (feet).

(g) WATER_DIST: Distance to the nearest body of water (feet).

(h) CNTR_DIST: Proximity to Miami’s central business district (feet).

(i) SUBCNTR_DI: Distance to the nearest subcenter (feet).

(j) HWY_DIST: Distance to the nearest highway (feet) - another noise indicator.

(k) Age: Age of the property (years).

(l) AVNO60PLUS: Dummy variable indicating if airplane noise exceeds acceptable levels.

(m) Structure_quality: Assessed quality of the building structure.

(n) Month_sold: The month the property was sold, recorded as 1 for January 2016.

(o) Latitude and Longitude: Geographic coordinates of the property.

### Data Preparation & Exploration
The overall histogram of the dependent variable is skewed to the right. This pattern suggests that while most properties fall within a lower price range, there are a few properties with significantly higher prices. 

![Snap_1](https://github.com/user-attachments/assets/4678e4f5-d84f-4bad-b71f-63d5c5dfe397)


The scatter plot visualization, provided below, further illustrates the distribution of data points and highlights the relationships between various features and the property prices.

![Snap_1](https://github.com/user-attachments/assets/2a596c11-5bca-4297-a1d9-168aa7555fa6)

The analysis reveals that the total living area exhibits the strongest correlation with the sale price of properties, suggesting it is a critical factor in determining housing values. Additionally, the value of special features, the quality of the structure, and the distance to the nearest subcenter also show significant positive correlations with the sale price, indicating their influence on property valuation in the Miami housing market.

![Snap_1](https://github.com/user-attachments/assets/8d4f126c-ca7c-4827-bf75-9fe620f9d4cc)



### Model Building 
The goal was to analyze how proximity to key features such as the ocean, central business district, and highways impacts the prices of homes in Miami. This involved data preprocessing, feature selection, and regression modeling, aiming to provide insights into how location affects housing costs.

The dataset to focus on seven key variables include: SALE_PRC, OCEAN_DIST, CNTR_DIST, HWY_DIST, RAIL_DIST, SPEC_FEAT_VAL, and WATER_DIST.

A correlation matrix was created to detect multicollinearity among variables. The analysis showed no significant multicollinearity, which is crucial for the validity of the regression models.

### First order model

Starting with a basic regression model, it was found that the model explained about 39.84% of the variation in housing prices, showing moderate explanatory power. The very low P-values pointed to significant relationships between variables. However, efforts to refine the model through backward selection led to a decrease in the adjusted R-squared with each variable removed, highlighting the complexity and interdependence of the factors influencing housing prices.

When the first-order model was used, it was discovered that 39% of the variability in Miami housing prices could be explained by the selected factors. However, a closer look at the residuals revealed heteroscedasticity, showing that the spread of the data's variability wasn't consistent. This suggests that the model may not adequately capture all the influencing elements or complexities of the housing market.

![Snap_1](https://github.com/user-attachments/assets/31ebfc8a-0519-44d1-a404-d5b11b79e4d9)

### Interaction Model
Interaction Model: Introduced an interaction term between OCEAN_DIST and WATER_DIST due to their conceptual similarity. This model improved the Adjusted R-square to 0.4025, slightly enhancing the explanatory power.
![Snap_1](https://github.com/user-attachments/assets/10ea6c73-e98b-47eb-8646-7f1db379f5c9)



![Snap_1](https://github.com/user-attachments/assets/0a17f441-1433-45a2-b042-3e835b1e3ac8)

### Second order Model

Second Order Model: Implemented to further explore complex relationships, which significantly improved the Adjusted R-square to 0.5577. However, patterns in the residuals indicated potential model overfitting or unaddressed non-linear relationships

![Snap_1](https://github.com/user-attachments/assets/6c46c636-0158-4930-a278-69c53afac6dc)

### Third Order model
The third-order regression model achieved an adjusted R-squared of 61.66%, indicating that it explained about 62% of the variability in Miami housing prices. This model marked a significant improvement in fit compared to simpler models. However, diagnostic evaluations revealed several concerns:

Residuals vs. Fitted Plot: The spread of residuals suggested heteroscedasticity, implying that errors varied with the level of fitted values.

Q-Q Plot: This plot showed that the residuals did not follow a normal distribution, particularly at the distribution's tails.

Residuals vs. Leverage Plot: Identified potential influential outliers which might impact the model's accuracy.

### Conclusions
Despite the improvements with more complex models, the presence of patterns in residual plots suggested potential overfitting. Overfitting occurs when a model is too closely fitted to the limited data, potentially making it inaccurate when predicting new or unseen data. Thus, I decided to adhere to the results of the first order model. Through this process, we concluded that while location-based factors significantly influence property prices, they alone cannot predict the full scope of housing prices in Miami. This realization underscores the complexity of real estate pricing and the need to possibly incorporate more diverse or extensive datasets for future analyses.


 
