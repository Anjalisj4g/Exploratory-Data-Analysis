# Exploratory Data Analysis
In this project, I have used various methods of exploratory data analysis detailing information about  the employees in various team based on a dataset from ABC company. The requirement of the company is to create a comprehensive report detailing information about their employees across various teams. 
## Features :
The dataset is all about the details of employees regarding their Name, Team, Number, Position, Age, Height, Weight, College and Salary. The dataset contains 458 rows and 9 columns. The aim of the project is metioned below : 
* Determine the distribution of employees across each team and calculate the percentage split relative to the total number of employees.
* Segregate employees based on their positions within the company.
* Identify the predominant age group among employees.
* Discover which team and position have the highest salary expenditure.
* Investigate if there's any correlation between age and salary.
* Represent all the above information visually.
### How it works
The project is done on  jupyter notebook. The language used is python. 
First of all, I have imported tools like numpy, pandas, matplotlib and seaborn. Then, the dataset is read as dataframe df. The dataset is given below :
http://localhost:8888/lab/tree/Entri_Class/Python/Assignments/ModuleEnd_Assignment/Employee_Report.csv

The first step is data preprocessing and checking for data consistency and integrity.
Data in 'Height' column is incorrect. So, I replaced it with random numbers between 150 and 180 using random function.

        __random_heights = np.random.randint(150, 181, size=len(df))__
        
The dataframe is checked for any null values and replaced them with 'Unknown'.
To determine the distribution of employees across each team, the value_counts function and sum function is applied in 'Team' column. Total number of employees in each team is derived.

        __print("Total Number of Employees =",df['Team'].value_counts().sum())__

To calculate the percentage split relative to the number of employees, number of employees in each team is represented in a pie chart with their respective percentages.
![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/21f2e38e-b4e2-4f56-80ef-d25072158ea9)

To segregate employees based on their positions within the company, value counts function is applied in 'Position' column. Total number of employees in each position is derived.

       __position_count=df['Position'].value_counts()__

The distribution of employees in each position is represented using a count plot.
![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/dff96679-16d9-495d-9ea1-8b745577cb1e)

To identify the predominant age group among the employees, they are grouped in age groups 18-25, 25-30, 30-35, 35-42 using the code below.
       __df['Age Group'] = pd.cut(df['Age'], bins=age_groups, labels=labels[:-1], right=False)
       age_group_counts = df['Age Group'].value_counts()
       predominant_age_group = age_group_counts.idxmax()__



