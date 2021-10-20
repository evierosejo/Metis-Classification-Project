# Classifying Energy Star Buildings in NYC

### Question
With the newly ubiquiotous public attention to the environmental impacts of our consumption-based economy, Realtor.com is looking to add a new filter into their property listing search engine to address sustainability when searching for a new home. Receiving an ENERGY STAR Certification indicates a building performs better in energy and water consumption than at least 75% of similar buildings nationwide. Enabling users to filter by buildings that are likely elegible to be ENERGY STAR certified will allow eco-conscious individuals to apply their values to the real estate search process, a feature not offered by competitors. 

In this project, I will develop a classification model to infer whether a building is elegible to be ENERGY STAR certified based on the most current NYC Department of Buildings data. 

### Data Description
Through New York City's public data platform, I have acquired 2020 [data and metrics](https://data.cityofnewyork.us/Environment/Energy-and-Water-Data-Disclosure-for-Local-Law-84-/usc3-8zwd) on energy and water consumption for Local Law 84 for buildings in NYC. This data set consists 28,067 buildings, either privately owned over 25,000 square feet or publicly owned over 10,000 square feet, each with data for 250 features. In order to predict ENERGY STAR Certification elegibility, I will be primarily working with energy and water consumption metrics, along with building descriptors and geospatial data. 

### Tools
Throughout this project, I will be using the following tools:
- SQL for querying in data
- Pandas for exploratory data analysis and feature engineering
- Matplotlib, seaborn and Tableau for visualizations
- Scikit-learn for classification and machine learning

### MVP Goal
I will develop visualizations that capture insights from the initial data exploration and create a model that effectively infers a building's eligibility for an ENERGY STAR Certification based on their energy and water consumption profile. 
