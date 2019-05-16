---
layout: page
title: Model And Conclusion
bigimg: /img/pubg4.jpg
---

## Prepare The Data For Machine Learning

The dataset was partitioned into 70% training set and 30% test set

Training set has a shape of (3111784, 44)


## First Random Forest Model

First Model has parameter 'n_estimators' = 60, 'min_samples_leaf" = 4, and 'max_features' = 0.5

The metric used to measure the model is Mean Absolute Error (MAE)

Result: MAE train is 0.033928063419654556, MAE test is 0.05548596242011615


## Feature Selection Using First Random Forest Model

```
feature_importances = pd.DataFrame({'Feature':X_train.columns, 'Importance':rfr_1.feature_importances_}
                       ).sort_values('Importance', ascending=False)
feature_importances[:15]
```
Select the top 15th most important features

![GW Data Science logo](/img/image_15.png)

Select features that have importance greater than 0.005


## Second Random Forest Model

Only use the selected features to train the model.

Result: MAE train is 0.033445120284611204, MAE test is 0.0565149285124814

Compare to the first model, the MAE decreases on the training set, but increases on the test set


## Recommendations

The size of the dataset is relatively large which caused some difficulties tuning the parameters of the model. Increasing the parameter “n_estimators” could improve the performance of the model. Also, applying cross validation and grid search to the model to tune other parameters could also improve the model, but could also cost huge amount of running time. Separating the solo mode data from the original dataset, and studying it individually could make a big difference. Overall, EDA and feature engineering are the two most important stages of the project. Tuning the parameters requires huge amount of time which is not very recommended.


## Conclusion

The best strategy to survive in the PUBG game is to avoid fighting. The result shows that walk distance contributes the most to the win placement percentage. The more distance a player walked directly results in a longer surviving time, which means the win placement percentage will go up. The ability to kill enemy players is the second most important factor. Whenever an enemy is eliminated, the player will be safer at the specific location. Boost item gives players the ability to heal and run faster. In conclusion, the three factors contribute the most to win a PUBG game. If a player has walked a long distance and managed to kill the enemies, there is a strong possibility that he or she could be the winner of the game.









