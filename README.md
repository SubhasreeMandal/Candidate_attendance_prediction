# **Candidate_attendance_prediction**
Companies often suffer from 'no show' of the candidates during interview. This project aims to predict the appearence of candidate during an interview based on previous dataset available. This model will help the companies to save their time and resources during an interview.

# Getting started

**Prerequisites**
1. Dataset (uploaded as Interview.csv)
2. Jupyter Notebook
3. Pip

Use **pip install** to install these-->

1. Seaborn
2. matplotlib
3. Numpy
4. Pandas
5. sklearn

**Langugae**

Python

**Executing the files**

1. Download the data set files and other python files and save then in one folder.
2. Open Jupyter Notebook and open interview attendance problem.ipynb file.
3. Run all the cells one by one.

**Workflow**

![image](https://user-images.githubusercontent.com/48086440/118094527-7adeaf00-b3ec-11eb-911b-957aab93b1c8.png)

**Collecting raw data**

Dataset for Candidate attendance problem is downloaded from Kaggle.

**Data cleaning**

After downloading the dataset, the dirty data needs to be cleaned. All the columnns with empty cells are dropped and columns are renamed to work smoothly. Mis-spelled words are replaced with the right spelled words.

**Exploratory data analysis**

The preliminary analysis of the data that gets the relations between the attributes and insights from the data using statistics and visualisation is called EDA or exploratory data analysis. EDA includes Missing value treatment, outlier treatment, variable transformation, variable creation, univariate analysis, bivariate analysis, multivariate analysis. in univariate analysis, there is one variable, distribution of which is shown using countplot. One example is shown below:

![image](https://user-images.githubusercontent.com/48086440/118098715-dbbcb600-b3f1-11eb-8be3-a62f003705e7.png)


In case of bivariate analysis, relation between two variable is observed here. One example is shown below:


![image](https://user-images.githubusercontent.com/48086440/118098907-24746f00-b3f2-11eb-9247-e0b4f3646e65.png)


 Correlation between all the columns, visualised using countplot helped in the Nan values filling process.

Here in the dataset, the data is of categorical value. That's why no outlier removal process is needed. But categorical data always has to be converted to numerical data. Model building is only possible with numeric type of data. The input variables, which have two unique values, is converted to numeric data using get_dummies. The input variable, with more that two unique values, are converted into numeric data using fit_transform. All the categorical data columns are dropped after that.

![image](https://user-images.githubusercontent.com/48086440/118096694-53d5ac80-b3ef-11eb-99df-3528cfe2eab6.png)


Now the data is ready for bulding models.

**Feature selection**

Data can suffer from curse of dimensionality. That means its not always true that high the feature more the accuracy.That's why feature selection is done here. First some models are created for testing purpose. Here wrapper method is used for feature selection. It can be done in two ways. First one is forward selection method. Here sample feature space is created by adding one by one features.

![image](https://user-images.githubusercontent.com/48086440/118102385-58ea2a00-b3f6-11eb-9480-f6dd487e7a89.png)


Another one is backward elimination method. Here original feature space is tested then removing one by in feature, the testing is done.

![image](https://user-images.githubusercontent.com/48086440/118102455-70c1ae00-b3f6-11eb-899b-5c4ed2ee4669.png)

**Model building**

First, models are built with all the features in the dataset. Then during feature selection, for each step, four classifiers are used.

1. Logistic regression
2. KNN classifier
3. Naive-Bayes classifier
4. Decision tree classifier 

Logistic regression is used because dataset had categorical value.

![image](https://user-images.githubusercontent.com/48086440/118108368-8a1a2880-b3fd-11eb-90b8-d67801d5481a.png)

![image](https://user-images.githubusercontent.com/48086440/118108436-9e5e2580-b3fd-11eb-9fe9-c31488a78cec.png)

![image](https://user-images.githubusercontent.com/48086440/118108454-a6b66080-b3fd-11eb-9696-be98a40314e4.png)

![image](https://user-images.githubusercontent.com/48086440/118108530-b8980380-b3fd-11eb-87af-22f048f6d673.png)


After model creation, performance of the models are evaluated using connfusion matrix, accuracy, precision, recall and f1 score. Recall is the best metric to evaluate performance of a model as it records nothe the true-positive and false-negative values.

**Ensemble learning**

In the end of model building, we have one logictic regression model with best recall, one decision tree classifier with best recall and as well as one KNN and Naive-Bayes classifier. All we have is some isolated learners. Isolated learners are always weak lerners. That's why we have created a model in a collaborative learning using VOTING which will perform better. One ensamble learner for the models during forward selection and one ensemble learner during backward elimination is built. 

![image](https://user-images.githubusercontent.com/48086440/118110222-c8184c00-b3ff-11eb-90ef-0dbb92168a07.png)

![image](https://user-images.githubusercontent.com/48086440/118110321-e54d1a80-b3ff-11eb-9407-5052626c6588.png)


**Model evaluation**

Best accuracy of the ensemble learner is 73%. This model can predict the candidate appearence with 73% accuracy.

