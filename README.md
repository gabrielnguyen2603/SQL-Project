# The World Bank Financial Analysis
The World Bank's IDA (International Development Association) Statement of Credits, Grants and Guarantees dataset provides a comprehensive view of financial assistance provided to developing countries. This dataset contains over 300MB of historical data covering all credits, grants, and guarantees provided since inception, with monthly snapshots from April 2011 to May 2025.

The primary purpose of creating an SQL project with this dataset is to analyze global development financing patterns and provide insights into how the World Bank supports poverty reduction efforts worldwide. The IDA provides development credits, grants and guarantees to recipient member countries at concessional rates to help meet their development needs

# Exploration 
For this project, I first use Python to preprocess the dataset, converting data types (such as dates and numeric fields) to ensure consistency and accuracy. I also rename features to more descriptive and standardized names for clarity and easier analysis. After cleaning and transforming the data, I load it into a MySQL database. MySQL is then used for structured querying and in-depth data analysis, allowing me to efficiently answer key business questions and uncover trends within the IDA funding dataset

Table preview of this dataset
![image](https://github.com/user-attachments/assets/ff55cc0e-f7d9-4140-9c4f-a579f5cd56a0)

# Key findings
- The finding that 51.38% (859 out of 1672) of projects have post-closure disbursements is a major red flag that points to systemic issues. This isn't a rare exception; it's happening in more than half of the portfolio.
  
- However, 2020 saw a massive spike in both commitments and the number of projects (58) due to the COVID-19 Pandemic, with total commitments reaching over $269 billion. In 2022, lending for natural disasters remained high, with commitments of nearly $170 billion for just 4 projects, indicating a focus on larger-scale disaster response initiatives.
  
- Sudan, across three different regional classifications (AFRICA EAST, AFRICA, and EASTERN AND SOUTHERN AFRICA), consistently shows a cancellation rate of 44.16%. This suggests significant challenges in project implementation or stability in that area. Other countries with notably high cancellation rates include Afghanistan (26.39%), Myanmar (19.02%), and Chad (appearing with both 18.06% and 15.34% rates). These high rates could point to political instability, administrative hurdles, or a re-evaluation of project viability.
  
- More recently, Nigeria (2023) and Ukraine (2024) have emerged as the highest-funded countries, likely due to recent economic and geopolitical events requiring substantial international support.

# Business Question 
- Which countries or regions have received the most IDA funding over time, and how has this changed since 2011?

- How have funding volumes responded to major global events, such as the COVID-19 pandemic or natural disasters?

- Which regions and countries show the highest credit cancellation rates? 

- What proportion of projects have disbursed funds after their closed date, and what does this indicate about project management or reporting lags?




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


In the below query, a significant 51.38% of projects have disbursed funds after their official closing date. This suggests a potential disconnect between the formal project closure and the final financial settlement.


<img width="888" height="602" alt="image" src="https://github.com/user-attachments/assets/93205819-6915-45b7-8f33-98331ab25793" />


(SQL Query)


<img width="559" height="51" alt="image" src="https://github.com/user-attachments/assets/f0bd70d7-03a7-48ce-ac3b-e4bcefc3c5cd" />


(Query Result)


      

