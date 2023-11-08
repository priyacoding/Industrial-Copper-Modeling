pip install xgboost
pip install matplotlib
pip install seaborn
pip install streamlit
```
**Usage**
To use this project, follow these steps:
1. Clone the repository: https://github.com/priyacoding/Industrial-Copper-Modeling.git 
2. Install the required packages: ```pip install -r requirements.txt```
3. Run the Streamlit app: ```streamlit run app.py```
**Features**
**Data Preprocessing:**
- **Data Understanding**: Before diving into modeling, it's crucial to gain a deep understanding of your dataset. Start by identifying the types of variables within it, distinguishing between continuous and categorical variables, and examining their distributions. In our dataset, there might be some unwanted values in the 'Material_Ref' feature that start with '00000.' These values should be converted to null for better data integrity.
- **Handling Null Values**: The dataset may contain missing values that need to be addressed. The choice of handling these null values, whether through mean, median, or mode imputation, depends on the nature of the data and the specific feature.
- **Encoding and Data Type Conversion**: To prepare categorical features for modeling, we employ ordinal encoding. This technique transforms categorical values into numerical representations based on their intrinsic nature and their relationship with the target variable. Additionally, it's essential to convert data types to ensure they match the requirements of our modeling process.
- **Skewness - Feature Scaling**: Skewness is a common challenge in datasets. Identifying skewness in the data is essential, and appropriate data transformations must be applied to mitigate it. One widely-used method is the log transformation, which is particularly effective in addressing high skewness in continuous variables. This transformation helps achieve a more balanced and normally-distributed dataset, which is often a prerequisite for many machine learning algorithms.
- **Outliers Handling**: Outliers can significantly impact model performance. We tackle outliers in our data by using the Interquartile Range (IQR) method. This method involves identifying data points that fall outside the IQR boundaries and then converting them to values that are more in line with the rest of the data. This step aids in producing a more robust and accurate model.
- **Wrong Date Handling**: In cases where some delivery dates are precedes the item dates, we resolve this issue by calculating the difference and it's used to train a Random Forest Regressor model, which enables us to predict the corrected delivery date. This approach ensures that our dataset maintains data integrity and accuracy.
**Exploratory Data Analysis (EDA) and Feature Engineering:**
- **Skewness Visualization**: To enhance data distribution uniformity, we visualize and correct skewness in continuous variables using `Seaborn's Histplot and Violinplot`. By applying the Log Transformation method, we achieve improved balance and normal distribution, while ensuring data integrity.
- **Outlier Visualization**: We identify and rectify outliers by leveraging `Seaborn's Boxplot`. This straightforward visualization aids in pinpointing outlier-rich features. Our chosen remedy is the Interquartile Range (IQR) method, which brings outlier data points into alignment with the rest of the dataset, bolstering its resilience.
- **Feature Improvement**: Our focus is on improving our dataset for more effective modeling. We achieve this by creating new features to gain deeper insights from the data while making the dataset more efficient. Notably, our evaluation, facilitated by `Seaborn's Heatmap`, confirms that no columns exhibit strong correlation, with the highest correlation value at just 0.42 (absolute value), underlining our commitment to data quality and affirming that there's no need to drop any columns.
**Classification:**

- **Success and Failure Classification**: In our predictive journey, we utilize the 'status' variable, defining 'Won' as Success and 'Lost' as Failure. Data points with status values other than 'Won' and 'Lost' are excluded from our dataset to focus on the core classification task.

- **Handling Data Imbalance**: In our predictive analysis, we encountered data imbalance within the 'status' feature. To address this issue, we implemented the SMOTETomek oversampling method, ensuring our dataset is well-balanced. This enhancement significantly enhances the performance and reliability of our classification tasks, yielding more accurate results in distinguishing between success and failure.

- **Algorithm Assessment**: In the realm of classification, our primary objective is to predict the catogorical variable of status. The dataset is thoughtfully divided into training and testing subsets, setting the stage for our classification endeavor. We apply various algorithms to assess their performance and select the most suitable base algorithm for our specific data.

- **Algorithm Selection**: After rigorous evaluation, the Extra Trees Classifier and Random Forest Classifier emerge as strong contenders, offering commendable testing accuracy. However, careful examination reveals overfitting in training accuracy. We opt for the Random Forest Classifier due to its balance between interpretability and accuracy.
- **Hyperparameter Tuning with GridSearchCV and Cross-Validation**: To fine-tune our model and mitigate overfitting, we employ GridSearchCV with cross-validation for hyperparameter tuning. This function allows us to systematically explore multiple parameter values and return the optimal set of parameters. 
`{'max_depth': 20, 'max_features': 'sqrt', 'min_samples_leaf': 1, 'min_samples_split': 2}`
- **Model Accuracy and Metrics**: With the optimized parameters, our Random Forest Classifier achieves an impressive 96.5% accuracy, ensuring robust predictions for unseen data. To further evaluate our model, we leverage key metrics such as the confusion matrix, precision, recall, F1-score, AUC, and ROC curve, providing a comprehensive view of its performance.
- **Model Persistence**: We conclude this phase by saving our well-trained model to a pickle file. This enables us to effortlessly load the model and make predictions on the status whenever needed, streamlining future applications.
**Regression:**
- **Algorithm Assessment**: In the realm of regression, our primary objective is to predict the continuous variable of selling price. Our journey begins by splitting the dataset into training and testing subsets. We systematically apply various algorithms, evaluating them based on training and testing accuracy using the R2 (R-squared) metric, which signifies the coefficient of determination. This process allows us to identify the most suitable base algorithm tailored to our specific data.
- **Algorithm Selection**: After thorough evaluation, two contenders, the Extra Trees Regressor and Random Forest Regressor, emerge with commendable testing accuracy. However, closer examination reveals overfitting in training accuracy. We opt for the Random Forest Regressor, as it strikes a balance between interpretability and accuracy, making it a fitting choice.
- **Hyperparameter Tuning with GridSearchCV and Cross-Validation**: To fine-tune our model and mitigate overfitting, we employ GridSearchCV with cross-validation for hyperparameter tuning. This function allows us to systematically explore multiple parameter values and return the optimal set of parameters.
`{'max_depth': 20, 'max_features': None, 'min_samples_leaf': 1, 'min_samples_split': 2}`.
- **Model Accuracy and Metrics**: With the optimized parameters, our Random Forest Regressor achieves an impressive 95.7% accuracy. This level of accuracy ensures robust predictions for unseen data. We further evaluate our model using essential metrics such as mean absolute error, mean squared error, root mean squared error, and the coefficient of determination (R-squared). These metrics provide a comprehensive assessment of our model's performance.
- **Model Persistence**: We conclude this phase by saving our well-trained model to a pickle file. This strategic move enables us to effortlessly load the model whenever needed, streamlining the process of making predictions on selling prices in future applications.
**Contributing**
Contributions to this project are welcome! If you encounter any issues or have suggestions for improvements, please feel free to submit a pull request.
**License**
This project is licensed under the MIT License. Please review the LICENSE file for more details.

