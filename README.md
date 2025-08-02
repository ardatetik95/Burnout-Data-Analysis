# Burnout-Data-Analysis
An analysis project using employee stress data to find out the key causes of burnout in a company.

Credits:
Dataset was taken from Kaggle.com
Link to dataset:
https://www.kaggle.com/datasets/ankam6010/synthetic-hr-burnout-dataset

Disclaimer: Every data part in this dataset is fictional and isn’t related in any way to a real person or company.

Scenario:
Kroeber, a fictional tech company with employees in Analyst, Sales, HR, Manager and Engineer roles.
Managers and HR employees got many reports about work stress and employees lowering performance.
To find out why the employee performance was getting lower, the company conducted a survey to calculate work satisfaction, stress and burnout levels of their employees.
Conducting research and putting survey results of 2000 employees in a file, Kroeber Tech Company hired you to conduct an analysis of the results.
The company is using Excel and Google Sheets as their main tool for reporting and analysis. They want you to prepare an interactive dashboard for Management and HR and present the data to them in an understandable manner.

About the Database:
<img width="985" height="464" alt="DB Info" src="https://github.com/user-attachments/assets/b2e0b034-aa72-4f57-b3a8-1402efee5fa8" />

Tasks:

1- Find out which employees are burnt out

2- Using the data you have, create a parameter and find out which employees are at the risk of being burnt out

3- Delve into working departments. Is there a department where burnout rates are different than others?

4- Does age, gender and experience have a role in stress?

5- Does office-remote work ratio have a role in stress?

6- Are there any correlations worth considering?

7- What are the main causes of the stress? How can we fix them?

Part 1: Altering the Data

1.1) Creating the BurnoutRisk column

To see which employees are close to being burnt out, we must adjust our data and use a formula to filter them out.

Our conditions are:
- StressLevel value is 5 or higher than 5
- SatisfactionLevel is lower than 3.0
- Burnout value isn’t 1

Database before we add the BurnoutRisk column, filtering data according to the parameters above
<img width="676" height="714" alt="image" src="https://github.com/user-attachments/assets/78845406-b816-477e-8d49-21c7d261a82d" />

Adding the BurnoutRisk column
<img width="893" height="848" alt="image" src="https://github.com/user-attachments/assets/ee26114b-738b-4e5d-8ee2-145a7402b013" />

Function written to generate BurnoutRisk column

=IF(AND(H2<3;I2>5;J2=0);1;0)

1.2) Creating the RemoteRole column

The RemoteRatio column shows how many hours does an employee work remotely. When calculated with WorkHoursPerWeek, we can find out how many hours did an employee work.

To use this column more effectively in our analysis, I decided to create a column called RemoteRole using these parameters:

Ratio between 0-9: Office Worker

Between 10-24: Mostly in Office	

Between 25-49: Hybrid

Between 50-74: Mostly Remote	

More than 75: Remote

Adding the RemoteRole Column
<img width="997" height="842" alt="image" src="https://github.com/user-attachments/assets/6b4afa26-ccee-40b7-85c7-f1fb1b95bee9" />

Function written to generate RemoteRole column

=IFS(AND(G4>=0; G4 <= 9); "Office Worker"; 
AND(G4 >= 10; G4 <= 24); "Mostly in Office"; 
AND(G4 >= 25; G4 <= 49); "Hybrid"; 
AND(G4 >= 50; G4 <= 74); "Mostly Remote"; 
G4 >= 75; "Remote" )

2) Visualizing our Data

2.1) General Informations about our Employees

<img width="1183" height="229" alt="General Stats" src="https://github.com/user-attachments/assets/a4104a50-f518-4633-9bb5-6667b4237d0d" />

Our burnout rate is 6.45, which makes up 129 out of 2000 employees
Burnout risk rate is 16.90, it makes up around 338 out of 2000 employees
Burnout and risk rate combined equals to 23,35%, which means around 1/4 of our employees are at risk

When we check the averages, we can see the rest of our employees have a stress score around 5.35-5.50. We can say most of our employees are mildly stressed.
Average satisfaction also dances around the median score
Average weekly work hours are around 49 hours, which makes up around 9-10 hours per day

2.2) Burnout Information of our Departments

<img width="1444" height="597" alt="Department Info" src="https://github.com/user-attachments/assets/0fd6227d-d2f0-4406-a58b-e587960ae804" />
Sales department has the highest burnout and highest risk rate. It is followed by HR and Manager roles.
Compared to those three departments, Analysts and Engineers seem to be having less burnout and under lower risk.

2.3) Burnout Information of Departments and Roles
<img width="1052" height="767" alt="fr" src="https://github.com/user-attachments/assets/904329a9-fea5-4d2d-9df8-067e8f1e122d" />

Hybrid HR and Sales workers, Mostly in Office HR and Managers, Mostly Remote HR and Sales workers, Office Working Analysts and Managers are the most stressed people. People who work Remote have approximately close stress rates.
Satisfaction rates dance around 3 for the most work roles except Remote. Remote Analysts and Office Working Engineers are the most dissatisfied employees.
Average working hours vary around 49-50 per week, with Remote being slightly higher.
When we filter to people who are burnt out or at the risk, we can see that average working hours increase to above average rates. If we make a rough calculation, we can say that these people work %83 more than their counterparts.

2.4) Important Correlations
<img width="1637" height="502" alt="cor" src="https://github.com/user-attachments/assets/8571dd26-2f73-4cf1-82e4-3940c18cc8fc" />

Burnout risk and rate is higher when the experience of the employee is around 0-2 years. Both rates tend to get lower once the 2 year threshold has been past.
As the working hours increase, burnout rates increase as well. Interestingly, risk rates decrease as work hours increase. Probably because most people are already burnt out at that rate.

3) Key Insights
- We can say that sex or age is not a factor for high stress levels and burnout.
- Employees with lower levels of experience, especially around 0-2 years are more prone to stress.
- Our burnt out employees work 2 hours more than average. This is highly correlated with low satisfaction and is the main cause of burnout
- People who work Remote, Mostly Remote or Hybrid are working 0.08 more than average. This lowers their satisfaction and increases stress.

4) Recommendable Actions
- Stress management training for new employees
- Lowering work hours by hiring more people or dividing work load equally
- Adjusting remote-office work styles in a more balanced way and according to the department's workload and needs.







