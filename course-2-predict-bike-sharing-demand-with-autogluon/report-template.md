# Report: Predict Bike Sharing Demand with AutoGluon Solution

Demirhan Demirkol

## Initial Training

### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?

Three distinct experiments were conducted as described:

1. Original Raw Submission [Model: initial]
2. Submission with Additional Features (EDA + Feature Engineering)
3. Hyperparameter Optimization (HPO)

Findings: Upon submitting predictions from these experiments, it was noted that some yielded negative prediction values. To comply with Kaggle's submission guidelines, which prohibit negative predictions, all such negative outputs from the respective predictors were substituted with zero.

### What was the top ranked model that performed?

The leading model was derived from the (add features) approach. It achieved a validation RMSE score of 33.3478 and the highest Kaggle score of 0.44187 on the test dataset. This model was crafted by leveraging exploratory data analysis (EDA) and feature engineering, without the aid of hyperparameter optimization.

## Exploratory data analysis and feature creation

### What did the exploratory analysis find and how did you add additional features?

The process included several steps:

1. The feature "datetime" was parsed as a datetime feature to extract hour information from the timestamp.
2. Independent features "season" and "weather" were initially read as integers. Recognizing them as categorical variables, they were converted into the category data type.
3. Feature extraction was performed to obtain separate independent features for year, month, day (dayofweek), and hour from the datetime feature. Consequently, the datetime feature was removed.
4. After thorough examination, it was observed that the features "casual" and "registered" significantly enhanced RMSE scores during cross-validation and exhibited strong correlation with the target variable "count". However, since these features were present only in the train dataset and not in the test data, they were disregarded/dropped during model training.

### How much better did your model preform after adding additional features and why do you think that is?

The model's performance saw improvement following these actions:

1. Conversion of specific categorical variables, initially represented as integer data types, into their true categorical data types.
2. Exclusion of "casual" and "registered" features during model training due to their absence in the test dataset.
3. Removal of "atemp" from the datasets due to its high correlation with another independent variable, "temp," thereby mitigating multicollinearity.
4. Utilization of feature extraction to split the "datetime" feature into multiple independent features such as year, month, day, and hour, along with the addition of "day_type." This refinement enhanced model performance by enabling better assessment of seasonality or historical patterns in the data.

## Hyper parameter tuning

### How much better did your model preform after trying different hyper parameters?

The Autogluon package was employed for training, adhering to the prescribed settings. However, the performance of hyperparameter-optimized models fell short of expectations due to limitations in the hyperparameter tuning process. These limitations arose from the fixed set of values provided by the user, which restricted the options Autogluon could explore.

During hyperparameter optimization with Autogluon, two crucial parameters, namely 'time_limit' and 'presets,' played significant roles. The 'time_limit' parameter, in particular, determined the duration within which Autogluon could build models. Insufficient time limits might lead to Autogluon's failure in constructing any models for the specified hyperparameters.

Moreover, the choice of presets, such as "high_quality" with auto_stack enabled, demanded substantial memory usage and computational resources, rendering them impractical within the prescribed time limits. Consequently, lighter and faster preset options like 'medium_quality' and 'optimized_for_deployment' were explored. Among these, the "optimized_for_deployment" preset was preferred for the hyperparameter optimization routine due to its faster and lighter nature, as other presets failed to generate models using Autogluon for the experimental configurations.

### If you were given more time with this dataset, where do you think you would spend more time?

Given more time to work with this dataset, I would like to explore additional potential outcomes by running AutoGluon for an extended period with a high-quality preset and enhanced hyperparameter tuning.

With this extended timeframe, AutoGluon can delve deeper into the dataset, allowing for a more exhaustive search through the hyperparameter space and the adoption of advanced techniques like model stacking and ensemble learning. The aim is to develop models that not only perform well on the training data but also generalize effectively to unseen data.

By optimizing hyperparameters more comprehensively, we can potentially uncover configurations that were missed during shorter runs. This could lead to models that are finely tuned to the dataset's characteristics and exhibit improved predictive performance.

Furthermore, with longer training times, AutoGluon can capture more intricate patterns and structures in the data, resulting in models that generalize better. This could manifest as improved performance on validation and test datasets, indicating a more robust model overall.

However, it's important to consider resource constraints such as computational power and memory availability. Running AutoGluon for an extended period with a high-quality preset may require substantial resources and longer training times, which could impact other tasks or experiments concurrently underway.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.

| model        | hpo1              | hpo2              | hpo3                                      | score   |
| ------------ | ----------------- | ----------------- | ----------------------------------------- | ------- |
| initial      | prescribed_values | prescribed_values | presets: 'high quality' (auto_stack=True) | 1.81971 |
| add_features | prescribed_values | prescribed_values | presets: 'high quality' (auto_stack=True) | 0.44187 |
| hpo          | GBM               | NN-TORCH          | presets: 'optimize_for_deployment'        | 0.537   |

### Create a line plot showing the top model score for the three (or more) training runs during the project.

TODO: Replace the image below with your own.![1717868326809](image/report-template/1717868326809.png)


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![1717868355122](image/report-template/1717868355122.png)


## Summary

The bike sharing demand prediction project extensively utilized the AutoGluon AutoML framework for Tabular Data, leveraging its full capabilities to create both stack ensembles and individually configured regression models automatically. This framework facilitated rapid prototyping of a baseline model and significantly improved results, particularly when combined with data from thorough exploratory data analysis (EDA) and feature engineering, even without hyperparameter optimization. By employing automatic hyperparameter tuning, model selection, ensembling, and architecture search, AutoGluon efficiently explored and exploited the best options available. However, it was observed that hyperparameter tuning with AutoGluon, especially without default settings or random parameter configurations, could be complex and highly dependent on factors such as time limits, prescribed presets, model families, and the range of hyperparameters to be tuned. Despite offering improved performance over the initial submission, hyperparameter tuning with AutoGluon did not surpass the model with EDA and feature engineering but no hyperparameter tuning.
