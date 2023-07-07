# Capstone 2
# Predicting Public Transportation Safety Risk

## Introduction

Nashville, TN built a 2.1 million square foot convention center in 2013 to host both local and international events, but limited public transportation options are available between the convention center and the airport.   The Nashville Department of Transportation and Multimodal Infrastructure is considering adding additional public transportation between the two to help reduce the pressure on the congested roadways.  They would like to understand the safety risk implications of doing so as part of their decision-making process.  

Using XGBoost Regressor on data aggregated to the date and the nation as a whole, I was able to achieve a MAPE of 4.8%. I tested four models on data aggregated to date and individual locations, and then also aggregated to date and individual modes, and evaluated the best models based on MAE and RMSE since MAPE was not available due to division by zero.  These models and aggregations provide insight into the most important features influencing the safety risk for the nation as a whole, those influencing the safety risk of individual locations, and those influencing the safety risk of each of the modes.

The resulting recommendation is that in terms of safety risk, Nashville would be better served by increasing service to one of its existing modes instead of adding an additional mode of transportation like light rail. 

## Aggregations

I utilized three different aggregations to learn about the features influencing safety risk.

### modeling_df
* aggregated to date and the nation as a whole
* gives a big picture of the features influencing safety risk for the whole nation

### modeling_df2
* aggregated to date and location
* allows us to compare the features influencing Nashville's safety risk and compare them to those aggecting other locations

### modeling_df3
* aggregated to date and mode
* allows us to examine safety risk for the individual modes of transportation

## Modeling

I tried four regression models on each of the three aggregations.  XGBoost Regressor was the top performing model for modeling_df (MAPE: 4.8%). MAPE was not possible for the second and third aggregation due to zeros in the target leading to division by zero.  K Neighbors Regressor was the top performing model for modeling_df2 in with a MAE of 0.395, but XGBoost also performed well with an MAE of 0.454. For the third aggregation, K Neighbors Regressor again has the best MAE (0.591) and also the best RMSE.  Randome Forest took second with an MAE of 0.680.  

## Recommendations

I am able to recommend Nashville not add light rail because the mode's safety risk ratio is higher than that of any of the other modes Nashville currently has.  Nashville should instead consider adding service to one of it's existing modes, of which CR (commuter rail) has the lowest safety risk ratio and MB (bus service) has the highest.
