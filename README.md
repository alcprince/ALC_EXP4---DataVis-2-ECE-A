# 2ECE - A: PA-4 - Data Wrangling and Data Visualization

<h6>
<i><u>About the files:</u></i><br>
<u>board2.csv</u>: 
  <br>&nbsp;   A .csv file containing the table indexes and values of the ECE Board Exam 2 dataset.<br><br>
<u>ALCANTARA_DataWrang and DataVis.ipynb</u>: 
  <br>&nbsp;   A Jupyter Notebook file for the assignment problem on Data Wrangling and Visualization and loads <i>ECE Problem Exam Problem</i>.<br>
</h6>

<b><h4>ECE Problem Exam Problem</h4></b>
<h5>1.) A Python script where by using data wrangling and visualization techniques, we make dataframes based on the conditions given below:</h5>
<br>

```python
import pandas as pd #Imports Panda Library.

eceboard = pd.read_csv('board2.csv') #Loads the 'board2.csv file'
eceboard

```
<h6>Using the filename INSTRU, have a dataframe where the values displayed has their "Track" set as 'Instrumentation', "Hometown" set as 'Luzon', and their "Electronics" score is greater than 70. The values that are qualified with the previous conditions displays the values of the columns "Name", "GEAS", and "Electronics". 
<br>
<br>
  
```python
Instru = eceboard.loc[(eceboard['Electronics'] > 70) &  #Locates all values in the Electronics column higher than 70.
                      (eceboard['Hometown'] == 'Luzon') & #Locates all values with 'Luzon' in the Hometown column 
                      (eceboard['Track'] == 'Instrumentation'), #Locates all values with 'Instrumentation' in the Track column.
                      ['Name', 'GEAS', 'Electronics']] #Displays only the columns Name, GEAS, and Electronics for those that fits all the conditions above.
```
<h6>Using the filename MINDY, have a dataframe where the values displayed has their "Gender" set as 'Female', "Hometown" set as 'Mindanao', and their "Average" score is greater or equal to 55. The values that are qualified with the previous conditions displays the values of the columns "Name", "Track", "Electronics", and "Average".
<br>
<br>

```python
#Making a new column called 'Average' displaying the Average scores of all the subjects in the ECE Board 2 Dataset.

eceboard['Average'] = eceboard[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) 
eceboard
```
<br>

```python
Mindy = eceboard.loc[(eceboard['Average'] >= 55) & #Locates all values that are above or equals to 55 in the Average column. 
                      (eceboard['Hometown'] == 'Mindanao') & #Locates all values with 'Mindanao' in the Hometown column 
                      (eceboard['Gender'] == 'Female'), #Locates all values with 'Female' in the Gender column.
                      ['Name', 'Track', 'Electronics']] #Displays only the columns Name, Track, and Electronics for those that fits all the conditions above.

```

<h5>2.) A script where by it creates a visualization on how different features namely "Track", "Gender", and "Hometown" affects the average scores of students.</h5>
<br>
<h6>The relationship between "Track" and the Average Score of the students.</h6>

```python

```
