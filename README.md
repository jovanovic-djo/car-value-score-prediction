## Data Science / Machine Learning AVNET Graduate Program - Project Documentation
###### Detailed project milestones guide is below brief overview
### Car Value Score Prediction (Option B - Classification Problem)
###### Through the following points, logic, thoughts and results of this project will be discussed and explained. <br /> As agreed with the mentor, the project structure follows a logical organization of directories rather than milestone-based segmentation, reflecting best practices in real-world data science projects.
#### Structure of the project (minor files excluded):
<img src="https://github.com/user-attachments/assets/6735c3a4-ca91-4f77-932d-8b02ec97b180" alt="Screenshot 2024-12-17 005823" width="560px" />

## Brief Overview of the Approach
#### Problem Understanding and Exploratory Data Analysis
- In this milestone, exploratory data analysis is done using several Python libraries
- Data had no missing values or inconsistencies
- Several relevant visualizations are created
#### Data Cleaning and Feature Engineering
- Ordinal and Label encodings are applied (scikit-learn) to a dataset with additional renaming of the columns
- No additional features are added
- Data is split into test and train sets which are additionally scaled using StandardScaler()
#### Model Development and Evaluation
- Six classification models are trained and saved in 2 types of format for reusability (.joblib and .pkl)
- Four metrics are used for model evaluation
- Hyperparameter tuning and cross-validation are implemented
- Feature importance and confusion matrix visualizations are stored in distinct directories
- Additional visualizations are generated for unique models (Decision Tree)
#### Visualization and Presentation
- For each model, including the optimized one, visualizations are generated
- A Confusion matrix is generated for every model
- Feature importance is generated for several models
- Note: Generation of the feature importance for some of the models was not reliable and suitable. Explanation is in the detailed guide.

## Detailed Milestones Guide
###### The purpose of this guide is to highlight the approach, directories and files for each milestone. <br /> As mentioned, the structure of the project is not organized by milestones, but instead by intuitive and practical structure.
### 1. Problem Understanding and Exploratory Data Analysis
- First step was to explore data files. Only usable files were dataset by itself and information about dataset.
- Both instances of data are saved in data/unclean directory.
- Dataset is in .csv format (car_dataset.csv) and information is converted into .md file so it can be interpreted as README file within /unclean directory.
- Notebook (Jupyter) for exploratory data analysis is created in /notebooks folder (exploratory_data_analysis.ipynb)
- Dataset is imported, and basic information and details about dataset is printed.
- Visualizations are created and saved into graphs/eda directory (eda - exploratory data analysis). Types of visualizations are:
  - Merged count of attributes through classes graph (bar plot): For each attribute, its distinct values are counted and showed in 6 graphs, one for each feature, along with one additional graph which represent score (class_value) values count in dataset
  - Merged proportion of attributes through classes graph (bar plot): Shows distribution of score values over features in proportion from 0-1. For each feature value, score occurrence is displayed on the bar
  - Separated count of attributes through classes graph (bar plot): Plot with similar output as the previous one, but instead, it separates bars and displays count instead of proportion of the distribution
  - Cramer's V (phi) correlation plot (heatmap): This visualization shows the strength of relationships between categorical variables, where darker colors indicate stronger correlations between features, helping identify which variables are most strongly related to the car's class value and to each other. Values range from 0 (no association) to 1 (perfect association), making it easy to spot the most influential features for predicting car classifications
  - Parallel coordinates plot (parcoord): Each vertical axis represents a different feature, and each line crossing through these axes represents a single car instance, with the line color indicating its classification (unacceptable, acceptable, very good and good). This shows patterns across multiple features simultaneously which combinations typically lead to specific classifications
##### Conclusion:
###### Values are evenly distributed along all features, which means every feature has same total number of distinct values (example: safety values are evenly distributed into low, mid and high, with total count of 576 per mentioned value)
###### Scores are uneven, and data samples for some score values (class_value = 'unacc') are drastically greater that other ones, which drives to conclusion that this dataset would need some enhacements in terms of additional data collection or better distribution of score values
###### Visualizations that are created are suitable for showcasing most important insights in dataset structure and value distribution
### 2. Data Cleaning and Feature Engineering
- For data cleaning, corresponding Jupyter notebook is created in /notebooks directory (data_preparation.ipynb)
- Dataset is imported and checked for null values or anomalies again.
- Ordinal and Label encoding is applied to dataset
- Several columns are renamed:
  - class_values => class_value
  - buying => price
  - persons => seats
- Opinion is that additional features would not enhance results and would not be relevant, so my approach does not involve additional features.
- Dataset is saved as .csv file into data/clean directory (dataset.csv)
- Regarding splitting dataset: this is done in model_training.ipynb file
##### Conclusion: 
###### Dataset was almost usable and clean from the beginning, with small enhancements like renaming columns and encoding, it aquired its usable shape
###### With the appliance of uppermentioned, dataset is succesfully prepared for splitting and further usage
###### Note: Creation of new features was not relevant for favorable results
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
- Model configurations are declared for hyperparameter tuning. The following models are included:
  - Logistic Regression
  - Random Forest
  - Decision Tree
  - Naive Bayes
  - K-Nearest Neighbors (in the project referred to as KNN)
  - Support Vector Classification (in the project referred to as SVC)
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
- Insights are generated through output reports and visualizations
- Report output for each model consists of the following:
  - Saved models directory locations
  - Model training time
  - Training time estimation and metrics values
  - Detailed classification report
- Visualizations are:
  - Confusion matrices
  - Feature importance graphs
  - Custom model visualizations (Decision Tree)
- Visualizations for confusion matrices are saved in graphs/confusion_matrices
- Visualizations for feature importance are saved in graphs/feature_importance
- Every model performance summary is displayed with best performed model labeled
- Best model is optimized using hyperparameter tuning and report is generated along with visualizations
- Insights on best model are as follows:
  - Best parameters
  - Best cross-validation score
  - Optimization time required
  - Saved optimized models location directories
  - Optimized model performance using uppermentioned metrics
  - Detailed classification report on optimized model
  - Generating visualizations for optimized model
- Saved models are in models/ directory, information about saved models:
 - For each model there is directory for its saved models
 - Two file formats are supported: .joblib and .pkl
 - Additional directory is generated for optimized models which are saved within it
##### Conclusion:
###### Best model was Decision Tree by every metric. 
###### Optimized feature importance graph showed that safety is the most important feature, it wins over the price by a glance.
###### Best parameters for the Decision Tree are: {'class_weight': 'balanced', 'criterion': 'entropy', 'max_depth': None, 'max_features': None, 'max_leaf_nodes': None, 'min_impurity_decrease': 0.0, 'min_samples_leaf': 1, 'min_samples_split': 2, 'splitter': 'best'}
###### Naive Bayes had the worst performance of them all over every metric

#### 4. Visualization and Presentation
- Visualizations are stored in graphs directory under several sub-directories:
  - eda (Exploratory Data Analysis)
  - confusion_matrices
  - feature_importance
  - other
- Explanation for purpose and content of each mentioned directory:
  - eda: Directory for storing visualizations of the first milestone. All visualizations for this directory are generated within notebooks/exploratory_data_analysis.ipynb
  - confusion_matrices: Directory for storing confusion matrix graphs for each of mentioned models as a part of model evaluation process
  - feature_importance: Directory for storing feature importance graphs for several models which purpose is to emphasize importance of each feature
  - other: Miscellaneous graphs and visualizations that are not part of a bigger visualization group
- Reasons behind selective feature importance generation:
  - SVC: It supports feature importance for linear kernel through coef_ attribute, and it is not available for non linear kernels (rbf, poly, sigmoid)
  - KNN: It is not suitable for direct feature importance (has no built in feature importance function). This is distance based algorithm which does not provide feature rankings
  - Naive Bayes: It also does not have direct feature importance mechanism. Class conditional probabilities could be evaluated, but not true feature importance
##### Conclusion: 
###### From the insights and all resulted visualizations, brief conclusion would be that there are several important features, besides that safety was the most important, maintenance and price are also important and should be considered, as they are affecting the final car value score the most

### Potential Enhancements
- Store functions in one or multiple util files from which they could be called and used, instead of storing them in notebooks.
- Additional diverse types of visualizations for better coverage of different aspects of the results.
- Splitting data into 3 data subsets would be favorable for future projects (train, test, validate)
- Write script to compose generated reports and valuable insights into distinct readable file

##### Additional approaches directory: Contains notebook with an alternative approach, where all of the models would be hyperparameter tuned, compared and stored along with the corresponding visualizations.
