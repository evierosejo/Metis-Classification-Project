# Predicting Energy Star Eligibility, a Random Forest Classifier

## Opportunity 
The goal of this project is to classify residential properties in NYC as eligible or ineligible for an ENERGY STAR certification, gaining insight on a building's sustainability profile. Realtor.com will thus enable site users to filter properties by ENERGY STAR eligibility, we will increase site traffic by offering more real estate listing information than competitors and attract individuals who are want to consider sustainability when renting or buying an apartment.

## Data Science Solution 

<details><summary>Impact hypothesis</summary>
<p> 
   We hypothesize that creating a classification model for ENERGY STAR eligibility will allow Realtor.com to make accurately predictions on how relatively energy and water efficient a building is. 
  
  **Primary Impacts:** classify buildings as ENERGY STAR certification eligible or ENERGY STAR certification ineligible, create a search filter based on whether a building is predicted to be eligible
  
  **Secondary Impacts:** increase traffic to website with search filters not offered by competing real estate listing websites, appeal to the growing audience concerned with their environmental impact 

</p>
</details>

<details><summary>Solution Path</summary>
<p> 
  
  Build a classification model to make predictions about eligibility for ENERGY STAR certifications for NYC residential buildings. 
 
</p>
</details>

## Data Description
Through New York City's open-source data platform, NYC OpenData, I acquired [Energy and Water Data Disclosure for Local Law 84 2021 (Data for Calendar Year 2020)](https://data.cityofnewyork.us/Environment/Energy-and-Water-Data-Disclosure-for-Local-Law-84-/usc3-8zwd) provided by NYC Mayor's Office of Climate and Sustainability. 
#### Data Specs
This dataset consists of 28,067 buildings, 18,751 of which have a primary property type categorization of multifamily housing based on a portfolio manager calculation. There were a total of 250 columns in this dataset; 64 relevant columns were used to build the classification models. 
#### Target and Features
* Target: ENERGY STAR Certification - Eligibility
* Examples of Investigated Features:
    * Weather Normalized Source EUI (kBtu/ft2)
    * Total GHG Emissions Intensity (kgCO2e/ft2)
    * Number of Bedrooms Density (Number per 1,000 sq ft)
    * Weather Normalized Site Natural Gas Intensity (therms/ft2)

## Algorithms
#### Data Cleaning and Feature Engineering 
I began by dropping the irrelevant columns, e.g. 'Property ID' and 'Supermarket/Grocery - Number of Open or Closed Refridgeration/Freezer Units', the columns which had all null values, and columns with the same data as another in a different unit or as the not weather normalized version, e.g. 'Source EUI (kBtu/ft²)' and 'Weather Normalized Source EUI (kBtu/ft²)'. I also dropped rows that had a construction status of 'Test' (n=31). 

Handling Missing Data: 
1. Converted 'Not Available' and 'Insufficient Access' string values to null values
2. Created a new column for the sum of null values in each row (mean=20)
3. Dropped rows with missing latitude or longitude values (n=583)
4. Converted null values to either 0 (n=21) or median (n=38) depending on the feature

Converting Categorical Features:
- Replaced 'Yes' and 'No' values with 1 and 0
- Changed multiclass categorical data to 1 and 0, with feature and without feature, respectively

#### Classification Modeling and Parameter Tuning 
##### Logistic Regression
After preprocessing the data, scaled with feature range of [0,1], I built a baseline logistic regression. This regression had an accuracy score of 0.88 and an ROC AUC score 0.80.

##### Decision Tree Classifier Model
The decision tree resulted in 1,533 nodes with a maximum depth of 28 with the following evaluation metrics:
* Accuracy: 0.87
* Recall: 0.75
* Precision: 0.75
* AUC ROC: 0.83

##### Random Forest Classifier Model 
I built a Random Forest with the original sample of data and a resampled dataset, since their was class imbalance of ~25% positive cases and ~75% negative cases in the training dataset. The model trained with the oversampled positive case dataset performed marginally better with evaluation metrics as follows:
* Accuracy: 0.92
* Recall: 0.85
* Precision: 0.84
* AUC ROC: 0.97

##### Bernoulli Naive Bayes
The last model built was a Naive Bayes model. This model was unable to classify the positive class and had the worst evaluation performance of the models built.

## Tools 
* SQL for database querying
* Pandas and Numpy for data acquisition, cleaning, and feature engineering
* Imblearn for resampling unbalanced classes 
* Sklearn for modeling and parameter tuning
* Matplotlib and Seaborn for data and model visualization

## Communication
In addition to this write up, I have created a Canva presentation. 
