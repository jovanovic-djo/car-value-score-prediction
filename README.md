## Data Science / Machine Learning AVNET Internship Project
###### Project structure understanding guide is below milestone approach explanation
### Car Value Score Prediction Project Documentation
###### Through the following points, we will discuss and explain logic, thoughts and results of this project. <br /> As agreed with the mentor, the project structure follows a logical organization of directories rather than milestone-based segmentation, reflecting best practices in real-world data science projects.
#### Structure of the project (minor files excluded):
<img src="https://github.com/user-attachments/assets/6735c3a4-ca91-4f77-932d-8b02ec97b180" alt="Screenshot 2024-12-17 005823" width="560px" />

#### Problem Understanding and Exploratory Data Analysis
- In this milestone exploratory data analysis is done using several Python libraries such as numpy, matplotlib, seaborn and pandas.
- Data had no missing values nor inconsistencies.
- Several visualizations are created using uppermetntioned libraries for values distribution insights.
- 
#### Data Cleaning and Feature Engineering
- Ordinal and Label encodings are applied (scikit-learn) to dataset with additional renaming of the columns.
- No additional features are added.
- Data is splited into test and train set which are additionally scaled using StandardScaler().
- 
#### Model Development and Evaluation
- Six classification models are trained and saved in 2 types of format for reusability (.joblib and .pickle).
- Four metrics are used for model evaluation.
- Hyperparameter tuning and cross-validation are implemented.
- Feature importance and confusion matrix visualizations are stored in distinct directories.
- Additional visualizations are generated for unique models (Decision Tree).
#### Visualization and Presentation

- For each model, including optimized one, visualizations are generated.
- Confusion matrix is generated for every model.
- Feature importance is generated for several models.

### Milestones Guide
###### The purpose of this guide is to highlight approach, directories and files for each milestone. <br /> As mentioned, structure of the project is not organized by milestones, but instead by intuitive and practical structure.
#### 1. Problem Understanding and Exploratory Data Analysis
- First step was to explore data files. Only usable files were dataset by itself and information about dataset.
- Both instances of data are saved in data/unclean directory.
- Dataset is in .csv format (car_dataset.csv) and information is converted into .md file so it can be interpreted as README file within /unclean directory.
- Notebook (Jupyter) for exploratory data analysis is created in /notebooks folder (exploratory_data_analysis.ipynb)
- Dataset is imported, basic information about dataset is printed.
- Visualizations are created and saved into graphs/eda directory (eda - exploratory data analysis). Types of visualizations are:
  - Merged count of attributes through classes graph (bar plot)
  - Merged proportion of attributes through classes graph (bar plot)
  - Separated count of attributes through classes graph (bar plot)
##### Conclusion: 
#### 2. Data Cleaning and Feature Engineering
- For data cleaning, corresponding Jupyter notebook is created in /notebooks directory (data_preparation.ipynb)
- Dataset is imported and checked for null values or anomalies again.
- Ordinal and Label encoding is applied to dataset
- Several columns are renamed:
  - class_values => class_value
  - buying => price
  - persons => seats
- Opinion is that additional features would not enhance results and would not be relevant, so my approach does not involve additional features.
- Dataset is saved as .csv file into data/clean directory (ordinal_encoded.csv)
- Regarding splitting dataset: this is done in model_training.ipynb file
##### Conclusion: 

#### 3. Model Development and Evaluation
- Several libraries and modules are imported and used:
  - pandas, numpy, matplotlib, seaborn
  - pickle, joblib, time, os
  - scikit-learn
- Scikit-Learned is used to import the following:
  - splitting data methods
  - model training methods
  - metrics
  - hyperparameter tuning implementation methods
  - visualization methods
- Metrics are:
  - f1 score
  - accuracy
  - precision
  - recall
- Model configurations are declared for hyperparameter tuning. Following models are included:
  - Logistic Regression
  - Random Forest
  - Decision Tree
  - Naive Bayes
  - K-Nearest Neighbors (in the project referred as KNN)
  - Support Vector Classification (in the project referred as SVC)
- For each model configuration, distinct model is declared along with multiple parameters.
- General purpose functions are declared, as follows:
  - Plot confusion matrix
  - Plot feature importance
  - Plot decision tree structure
  - Save model
  - Model metrics evaluation function
  - Evaluate all models
  - Apply hyperparameter tuning
  - Optimization of the model
- Evaluation of all models is executed
- Insights are generated through output report and visualizations
- Report output for each model consists of the following:
  - Saved models directory locations
  - Model training time
  - Training time estimation and metrics values
  - Detailed classification report
- Visualizations are:
  - Confusion matrices
  - Feature importace graphs
  - Custom model visualizations (Decision Tree)
- Visualizations for confusion matrices are saved in graphs/confusion_matrices
- Visualizations for feature importance are saved in graphs/feature_importance
- All models performance summary is displayed with best performed model labeled
- Best model is optimized using hyperparameter tuning and report is generated along with visualizations
- Insights on best model are as follows:
  - Best parameters
  - Best cross-validaiton score
  - Optimization time required
  - Saved optimized models location directories
  - Optimized model performance using uppermentioned metrics
  - Detailed classification report on optimized model
  - Generating visualizations for optimized model


##### Conclusion: 

#### 4. Visualization and Presentation
##### Conclusion: 

##### Additional approaches directory: Contains notebook with alternative approach, where all of the models would be hyperparameter tuned, compared and stored along with corresponding visualizations.


### Potential Enhancements
- Store functions in utils file from which they could be called and used, instead of storing them in notebooks.
- Diverse types of visualizations for better coverage of different aspects of the results.
- Splitting data into 3 data subsets would be favourable for future projects (train, test, validate)

