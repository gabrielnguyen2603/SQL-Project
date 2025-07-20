# The World Bank Financial Analysis
The World Bank's IDA (International Development Association) Statement of Credits, Grants and Guarantees dataset provides a comprehensive view of financial assistance provided to developing countries. This dataset contains over 300MB of historical data covering all credits, grants, and guarantees provided since inception, with monthly snapshots from April 2011 to May 2025.

The primary purpose of creating an SQL project with this dataset is to analyze global development financing patterns and provide insights into how the World Bank supports poverty reduction efforts worldwide. The IDA provides development credits, grants and guarantees to recipient member countries at concessional rates to help meet their development needs

# Exploration 
For this project, I first use Python to preprocess the dataset, converting data types (such as dates and numeric fields) to ensure consistency and accuracy. I also rename features to more descriptive and standardized names for clarity and easier analysis. After cleaning and transforming the data, I load it into a MySQL database. MySQL is then used for structured querying and in-depth data analysis, allowing me to efficiently answer key business questions and uncover trends within the IDA funding dataset

Table preview of this dataset
![image](https://github.com/user-attachments/assets/ff55cc0e-f7d9-4140-9c4f-a579f5cd56a0)

# Business Question: 
- Which countries or regions have received the most IDA funding over time, and how has this changed since 2011?

- How have funding volumes responded to major global events, such as the COVID-19 pandemic or natural disasters?

- Which regions and countries show the highest credit cancellation rates? 





# Analysis 

At first, i start to find out which nations or areas have benefited the most from IDA money over time, and how has this altered since 2011. I determined the top IDA funding recipient for each year since 2011 by writing a query that first aggregates the total original funding amount for each country-year. Then, I ranked the countries within each year by their funding amounts using a descending row number. By selecting only the rows where the rank equals one, I isolated the highest-funded recipient for each year. Finally, I arranged the results chronologically to provide a clear, year-by-year leaderboard of funding recipients.

![image](https://github.com/user-attachments/assets/7ed433fc-88a5-4808-981a-79b5aaefa8d2)


(SQL Query)


![image](https://github.com/user-attachments/assets/a8e67874-71f7-4c95-94ab-9aaf6d45c1b6)

(Query Result)

Move on to question 2, I look at each project and check when it was approved. If it was approved in 2020, we call it a “COVID-19 Pandemic” project. If the project’s name has the word “disaster” or “emergency,” we call it a “Natural Disaster” project. If it’s neither of those, we just call it a “Regular” project. Then, i count and add up all the projects for each group.

![image](https://github.com/user-attachments/assets/f1f9b4ed-e682-439a-8191-e40381db8f0b)


(SQL Query)


![Screenshot 2025-07-10 184432](https://github.com/user-attachments/assets/7b567a1d-9087-4781-8d95-331aa3b4fc4d)


(Query Result)

Let's move to next question, at first i analysed credit data, grouping by region and coutry. For each area, i counted unique credits, summed cancelled amounts, and total original amounts. Furthermore, calculated cancellation rate percent, safely handling zero data, and show the top 10 areas by cancellation rate, highlighting where to prioritize attention . 

<img width="959" height="440" alt="image" src="https://github.com/user-attachments/assets/482d76e3-1aeb-49c2-9015-1c638b1b2faa" />


(SQL Query)


<img width="993" height="246" alt="image" src="https://github.com/user-attachments/assets/d9ccaa99-8cf8-44a6-a84b-4501f0fcb0cc" />


(Query Result)




      

