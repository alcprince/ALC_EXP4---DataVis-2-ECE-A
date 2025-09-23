# 2ECE - A: PA-4 - Data Wrangling and Data Visualization

<h6>
<i><u>About the files:</u></i><br>
<u>board2.csv</u>: 
  <br>&nbsp;   A .csv file containing the table indexes and values of the ECE Board Exam 2 dataset.<br><br>
<u>ALCANTARA_DataWrang and DataVis.ipynb</u>: 
  <br>&nbsp;   A Jupyter Notebook file for the assignment problem on Data Wrangling and Visualization and loads <i>ECE Exam Problem</i>.<br>
</h6>

<b><h4>ECE Exam Problem</h4></b>
<h5>1.) A Python script where by using data wrangling and visualization techniques, we make dataframes on the file 'board2.csv' based on the conditions given below:</h5>
<br>

```python
import pandas as pd #Imports Panda Library.

eceboard = pd.read_csv('board2.csv') #Loads the 'board2.csv file'
eceboard

```
<h6>1. Using the filename INSTRU, have a dataframe where the values displayed has their "Track" set as 'Instrumentation', "Hometown" set as 'Luzon', and their "Electronics" score is greater than 70. The values that are qualified with the previous conditions displays the values of the columns "Name", "GEAS", and "Electronics". 
<br>
<br>
  
```python
Instru = eceboard.loc[(eceboard['Electronics'] > 70) &  #Locates all values in the Electronics column higher than 70.
                      (eceboard['Hometown'] == 'Luzon') & #Locates all values with 'Luzon' in the Hometown column 
                      (eceboard['Track'] == 'Instrumentation'), #Locates all values with 'Instrumentation' in the Track column.
                      ['Name', 'GEAS', 'Electronics']] #Displays only the columns Name, GEAS, and Electronics for those that fits all the conditions above.
```
<h6>2. Using the filename MINDY, have a dataframe where the values displayed has their "Gender" set as 'Female', "Hometown" set as 'Mindanao', and their "Average" score is greater or equal to 55. The values that are qualified with the previous conditions displays the values of the columns "Name", "Track", "Electronics", and "Average".
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

```python
import matplotlib.pyplot as plt #Imports MatPlot Library for Data Visualization.
```
<h6>The relationship between "Track" and the Average Score of the students.</h6>

```python
average1 = eceboard.groupby('Track')['Average'].mean()  #Groups the Track and Average column.

average1.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Track on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Track') #Labels the x-axis as the Track.
plt.show() #Shows the bar graph.
```

<h6>The relationship between "Gender" and the Average Score of the students.</h6>

```python
average2 = eceboard.groupby('Gender')['Average'].mean() #Groups the Gender and Average column.

average2.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Gender on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Gender') #Labels the x-axis as the Gender.
plt.show() #Shows the bar graph.
```

<h6>The relationship between "Hometown" and the Average Score of the students.</h6>

```python
average3 = eceboard.groupby('Hometown')['Average'].mean() #Groups the Hometown and Average column.

average3.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Hometown on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Hometown') #Labels the x-axis as the Hometown.
plt.show() #Shows the bar graph.
```
