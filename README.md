# Click-Through-Rate-Prediction

This repository contains a Python project that involves predicting whether a user would click on an online advertisement based on their interaction data. The project focuses on exploratory data analysis (EDA), data preprocessing, feature engineering, and training classical machine learning models to predict the `Clicked on Ad` target variable. All of the project's code can be found in `Click-Through Rate Prediction.ipynb`.


## Dataset
This dataset is comprised of 10000 records of users interacting with online advertisements, containing information in 10 different columns. It can be found [here](https://www.kaggle.com/datasets/swekerr/click-through-rate-prediction). The dataset is also available in the `dataset/` directory of this repository and will be automatically downloaded if the notebook file is run.

The `Click-Through Rate Prediction - Report.pdf` file contains Various visualizations, including bar plots, pie charts, histograms, and heatmaps, to explore the dataset and its features. Data preprocessing has been performed on the dataset, removing duplicate and outlier records. No null or missing values were found in the dataset, so no data imputation was necessary.

The dataset consists of the following attributes:
<br>Daily Time Spent on Site - Age - Area Income - Daily Internet Usage - Ad Topic Line - City - Gender - Country - Timestamp - Clicked on Ad


## Feature Engineering and Encoding

Several new features were engineered:
- **Percentage of Daily Time Spent on Site**: The ratio of time spent on the site to total daily internet usage.
- **Age Over 35**: A binary feature indicating whether the user is over 35.
- **DateTime Features**: Extracted `Day`, `Month`, `Day of Week`, and `Hour` from the `Timestamp`.
- **Time Segment**: Divided the day into four segments (0-6, 6-12, 12-18, 18-24).

Non-numerical features were one-hot encoded, including `Gender`, `Country`, `City`, and `Ad Topic Line`, creating over 1000 new features.


### Feature Scaling

To avoid data leakage, a train-test split was performed before scaling. High variance features, such as `Area Income`, were scaled using a preprocessor. A pipeline was created to ensure proper scaling during cross-validation using a Repeated Stratified K-fold technique.


## Model Results

Four classical machine learning models were trained on the dataset. Cross-validation was applied to each model, and scaling was essential for improving performance. Support Vector Classifier benefited from applying PCA. The best cross-validation accuracy for each model is as follows:
- **Random Forest Classifier**: 88.4% (No PCA)
- **Logistic Regression**: 89.3% (No PCA)
- **Naive Bayes**: 85.1% (No PCA)
- **Support Vector Classifier**: 83.7% (PCA applied)

Logistic Regression achieved the highest accuracy of 89.3%, proving to be the best model for this project.


## License
This project is licensed under the Apache 2.0 License - see the [LICENSE](LICENSE) file for details.


