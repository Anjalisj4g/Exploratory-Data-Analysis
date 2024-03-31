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
        
The dataframe is checked for any null values and replaced them with 'Unknown'.

To determine the distribution of employees across each team, the value_counts function and sum function is applied in 'Team' column. Total number of employees in each team is derived.

        print("Total Number of Employees =",df['Team'].value_counts().sum())

To calculate the percentage split relative to the number of employees, number of employees in each team is represented in a pie chart with their respective percentages.

        plt.pie(Teams, labels=Teams.index, autopct='%1.1f%%',startangle=140)
        
![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/21f2e38e-b4e2-4f56-80ef-d25072158ea9)

To segregate employees based on their positions within the company, value counts function is applied in 'Position' column. Total number of employees in each position is derived.

       position_count=df['Position'].value_counts()

The distribution of employees in each position is represented using a count plot.
![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/ee43ae86-4b21-4038-9591-0cd8c0b24f6c)

To identify the predominant age group among the employees, they are grouped in age groups 18-25, 25-30, 30-35, 35-42 using the code below.
      
       df['Age Group'] = pd.cut(df['Age'], bins=age_groups, labels=labels[:-1], right=False)
       age_group_counts = df['Age Group'].value_counts()
       predominant_age_group = age_group_counts.idxmax()

To represent employees in age groups, histogram is used.

![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/4ec4b7bd-dd45-483a-b4fb-d665a196d521)

To discover the team and position with highest salary expenditure, group employees based on teams and position separately by groupby function.

        grouped_by_team = df.groupby('Team')['Salary'].sum().reset_index()
        grouped_by_position = df.groupby('Position')['Salary'].sum().reset_index()

Now, take the maximum value of employees in team and position to find the team and position with highest salary expenditure.

        max_salary_team = grouped_by_team.loc[grouped_by_team['Salary'].idxmax()]
        max_salary_position = grouped_by_position.loc[grouped_by_position['Salary'].idxmax()]

To represent this graphically, bar graph is used.

![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/37c1d837-fcd3-4931-855d-032f398d3324)

![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/1b867d44-6437-4899-ad26-1df5eb10500d)

To investigate if there is any correlation between Age and Salary, corr() function is applied. Using this function, we can create a Correlation Matrix of employee details.

![image](https://github.com/Anjalisj4g/Exploratory-Data-Analysis/assets/162909803/438792e1-b73a-4aac-899d-5bd370e8dda5)

## Insights
* Most number of employees are in team New Orleans Pelicans with 4.1% of the total number of employees followed by team Memphis Grizzlies with 3.9%.
* Most number of employees are in position SG followed by position PF. The least number of employees are in position C.
* Employees of age group 25-30 are the predominant group followed by age group 18-25. Employees of age group 35-40 are least dominant in the data.
*  Team with Highest Salary Expenditure is Memphis Grizzlies and team with Least Salary Expenditure is Orlando Magic. Also, Position with Highest Salary Expenditure is PF and position with least Salary Expenditure is C.
*  From the correlation matrix, the correlation coefficient of age and salary is exactly 1. This means that there is a strong positive linear relationship between these two variables. This indicates that as age increases, salary also increases proportionally and vice-versa. Through this relationship, we can predict the salary of an employee by knowing his/her age. 






