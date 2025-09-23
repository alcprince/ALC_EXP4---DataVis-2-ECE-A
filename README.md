# 2ECE - A: PA-4 - Data Wrangling and Data Visualization

<h6>
<i>About the files:</i><br>
<ins>board2.csv</ins>: 
  <br>&nbsp;   A .csv file containing the table indexes and values of the ECE Board Exam 2 dataset.<br><br>
<ins>ALCANTARA_DataWrang and DataVis.ipynb</ins>: 
  <br>&nbsp;   A Jupyter Notebook file for the assignment problem on Data Wrangling and Visualization and loads <i>ECE Exam Problem</i>.<br>
</h6>


<b><h2>ECE Exam Problem</h2></b>

1). A Python script where by using data wrangling and visualization techniques, we make dataframes on the file <ins>'board2.csv'</ins> based on the conditions given below:

```python
import pandas as pd #Imports Panda Library.

eceboard = pd.read_csv('board2.csv') #Loads the 'board2.csv file' for easy viewing in the Jupyter Notebook.
eceboard

```
<h5>CONDITION 1: Using the filename INSTRU, have a dataframe where the values displayed has their "<ins>Track</ins>" set as '<i>Instrumentation</i>', "<ins>Hometown</ins>" set as '<i>Luzon</i>', and their "<ins>Electronics</ins>" score is greater than 70. 
  
<br><br>
The values that are qualified with the previous conditions displays the values of the columns "<ins>Name</ins>", "<ins>GEAS</ins>", and "<ins>Electronics</ins>". </h5>
  
```python
Instru = eceboard.loc[(eceboard['Electronics'] > 70) &  #Locates all values in the Electronics column higher than 70.
                      (eceboard['Hometown'] == 'Luzon') & #Locates all values with 'Luzon' in the Hometown column 
                      (eceboard['Track'] == 'Instrumentation'), #Locates all values with 'Instrumentation' in the Track column.
                      ['Name', 'GEAS', 'Electronics']] #Displays only the columns Name, GEAS, and Electronics for those that fits all the conditions above.
```

<h6>The desired output for INSTRU should look like and have this values:</h6>
<img width="217" height="129" alt="image" src="https://github.com/user-attachments/assets/410fa877-b6d0-4ccf-8abd-6c42b5e6c987" />

<h5>CONDITION 2: Using the filename MINDY, have a dataframe where the values displayed has their "<ins>Gender</ins>" set as '<i>Female</i>', "<ins>Hometown</ins>" set as '<i>Mindanao</i>', and their "<ins>Average</ins>" score is greater or equal to 55. 
  
<br><br>
The values that are qualified with the previous conditions displays the values of the columns "<ins>Track</ins>", "<ins>Electronics</ins>", and "<ins>Average</ins>". </h5>

```python
#Making a new column called 'Average' displaying the Average scores of all the subjects in the ECE Board 2 Dataset.

eceboard['Average'] = eceboard[['Math', 'Electronics', 'GEAS', 'Communication']].mean(axis=1) 
eceboard
```

```python
Mindy = eceboard.loc[(eceboard['Average'] >= 55) & #Locates all values that are above or equals to 55 in the Average column. 
                      (eceboard['Hometown'] == 'Mindanao') & #Locates all values with 'Mindanao' in the Hometown column 
                      (eceboard['Gender'] == 'Female'), #Locates all values with 'Female' in the Gender column.
                      ['Name', 'Track', 'Electronics']] #Displays only the columns Name, Track, and Electronics for those that fits all the conditions above.

```
<h6>The desired output for MINDY should look like and have this values:</h6>
<img width="280" height="192" alt="Image" src="https://github.com/user-attachments/assets/89b1d094-4ba9-487d-915e-09dfa9308327" />

<br>

---
2). A script where by it creates a visualization on how different features namely "Track", "Gender", and "Hometown" affects the average scores of students.

```python
import matplotlib.pyplot as plt #Imports MatPlot Library for Data Visualization.
```
* <h5><ins>The relationship between "Track" and the Average Score of the students.</ins></h5>

```python
average1 = eceboard.groupby('Track')['Average'].mean()  #Groups the Track and Average column.

average1.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Track on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Track') #Labels the x-axis as the Track.
plt.show() #Shows the bar graph.
```

<h6>With this codes above, the graph between the relationship of the track and average score is this:</h6>
<img width="624" height="551" alt="Image" src="https://github.com/user-attachments/assets/5676b17e-b0e1-4cfa-80fc-8d7f188e84e4" />

* <h5><ins>The relationship between "Gender" and the Average Score of the students.</ins></h5>

```python
average2 = eceboard.groupby('Gender')['Average'].mean() #Groups the Gender and Average column.

average2.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Gender on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Gender') #Labels the x-axis as the Gender.
plt.show() #Shows the bar graph.
```

<h6>With this codes above, the graph between the relationship of the gender and average score is this:</h6>
<img width="630" height="489" alt="Image" src="https://github.com/user-attachments/assets/85f0e3c2-05e8-4da6-9601-b2c443e02df0" />

*<h5><ins>The relationship between "Hometown" and the Average Score of the students.</ins></h5>

```python
average3 = eceboard.groupby('Hometown')['Average'].mean() #Groups the Hometown and Average column.

average3.plot(kind="bar") #Sets the relationship as a bar graph.
plt.title('Hometown on Average Score') #Title of the bar graph.
plt.ylabel('Average Score') #Labels the y-axis as the Average Score.
plt.xlabel('Hometown') #Labels the x-axis as the Hometown.
plt.show() #Shows the bar graph.
```
<h6>With this codes above, the graph between the relationship of the hometown and average score is this:</h6>
<img width="680" height="523" alt="Image" src="https://github.com/user-attachments/assets/5765b308-7e1c-4454-b855-ae003f966da2" />

