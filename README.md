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
        random_heights = np.random.randint(150, 181, size=len(df))
The, the dataframe is checked for any null values and replaced them with 'Unknown'.
To determine the distribution of employees across each team, the value_counts function and sum function is applied in 'Team' column.
        print("Total Number of Employees =",df['Team'].value_counts().sum())
