# Overview
## Objectives
1. Python review, introduction to GitHub
2. Downloading/installing course software
3. Introduction to data types (nominal, ordinal, categorical, rational)
4. Data collection and storage


## Skill Development
* **Data Science Principles:** understand data science workflow and applications, data types, metadata
* **Coding:** assign and manipulate data in python
* **Data Visualization:** create basic plots in python using Numpy
* **Professional:** create/use personal GitHub, clone content, customize markdown


# Deliverables
## 1. DataCamp Assignments
* Sign up for a class DataCamp account [with this link](https://www.datacamp.com/groups/shared_links/3312cfd78acb27a8fcb9593b540119e6b6232fde2050f31ab675a1dfcc9252d4), **using your UARK email**
* Complete the assigned **DataCamp courses** by logging in to *DataCamp > Organizations > My Assignments*:
    * [Introduction to Python](https://learn.datacamp.com/courses/intro-to-python-for-data-science)
        * Basic python concepts and definitions
        * Working with lists, functions, and packages
    * [Data Science for Everyone](https://learn.datacamp.com/courses/data-science-for-everyone)
        * Defining data science, workflows, and careers
        * Data collection and storage
        * Data preparation, exploration, and visualization
        * Experimentation and prediction methods


## 2. Case Study: 20,000 Board Games

* Pull and complete the [Case Study notebook](https://git.uark.edu/dasc-2113/module-01/-/blob/master/Case_Study_-_20_000_Board_Games_-_Student.ipynb) starter code & your assigned dataset from the [data folder](https://git.uark.edu/dasc-2113/module-01/-/tree/master/Data) (both contained in this repository--see above) 
    * For each exercise in the case study, write and run the appropriate code to find the answer.
    * Save and commit your finished assignment back to the master branch. 

## 3. Skill Assessment: Bayou Meto Lidar Quality Assessment (ungraded)
* Pull the csv file BayouMeto_LiDAR_QA.csv file from the Data folder in this project.
    * This file contains the locations of 40 or so check points that will be used to assess the quality of the height measured by a airborne LiDAR (`LidarZ` column) against a high-precision GPS measurment (`GPSZ`). The file contains a uniqued check point id (`ID`) and a `Region` column indicating two separate collection campaigns, and a `LandCover` column indicating the type of land cover over the check point. 
* Perform the following analyses in the most efficient way you know using the Python skills you learned in Introduction to Programming
    * Read the data file 
    * Plot the locations of the check poionts (the `X` and `Y` columns)
    * Compute and print the mean and standard deviation of the differences between the `Lidar-Z` and `GPS-Z` measurements.
    * Compute and print the mean and standard deviation of the differences between the `LiDAR-Z` and `GPS-Z` measurements by `Region`. 
    * Compute and print the mean and standard deviation of the differences betweent the `LiDAR-Z` and `GPS-Z` measurements by `LandCover`.
    * Qualitatively assess, in a comment section in your script, whether measurement quality is affected by `Region` or `LandCover`
    * Create a plot of your choice to illustrate your assessment.
* Deliver your answers in the form of a documented Python script 

