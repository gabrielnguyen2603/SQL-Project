# The World Bank Financial Analysis
The World Bank's IDA (International Development Association) Statement of Credits, Grants and Guarantees dataset provides a comprehensive view of financial assistance provided to developing countries. This dataset contains over 300MB of historical data covering all credits, grants, and guarantees provided since inception, with monthly snapshots from April 2011 to May 2025.

The primary purpose of creating an SQL project with this dataset is to analyze global development financing patterns and provide insights into how the World Bank supports poverty reduction efforts worldwide. The IDA provides development credits, grants and guarantees to recipient member countries at concessional rates to help meet their development needs

# Exploration 
For this project, I first use Python to preprocess the dataset, converting data types (such as dates and numeric fields) to ensure consistency and accuracy. I also rename features to more descriptive and standardized names for clarity and easier analysis. After cleaning and transforming the data, I load it into a MySQL database. MySQL is then used for structured querying and in-depth data analysis, allowing me to efficiently answer key business questions and uncover trends within the IDA funding dataset

Table preview of this dataset
![image](https://github.com/user-attachments/assets/ff55cc0e-f7d9-4140-9c4f-a579f5cd56a0)

# Business Question: 
- Which countries or regions have received the most IDA funding over time, and how has this changed since 2011?

- What is the distribution of funding types (credits, grants, guarantees) across different countries, and what patterns emerge?

- How have funding volumes responded to major global events, such as the COVID-19 pandemic or natural disasters?

- Which sectors or project types have attracted the largest share of IDA resources, and how has this evolved?

- What is the trend in outstanding debt or obligations to the IDA by country or region?

- Are there countries that have shifted from primarily receiving grants to credits or vice versa, and what might explain these transitions?

- How many new projects are approved each year, and what is the average size of these commitments?

- What are the top-performing or most impactful projects, and what lessons can be drawn from their outcomes?

# Analysis 

At first, i start to find out which nations or areas have benefited the most from IDA money over time, and how has this altered since 2011. I determined the top IDA funding recipient for each year since 2011 by writing a query that first aggregates the total original funding amount for each country-year. Then, I ranked the countries within each year by their funding amounts using a descending row number. By selecting only the rows where the rank equals one, I isolated the highest-funded recipient for each year. Finally, I arranged the results chronologically to provide a clear, year-by-year leaderboard of funding recipients.

![image](https://github.com/user-attachments/assets/7ed433fc-88a5-4808-981a-79b5aaefa8d2)


(SQL Query)


![image](https://github.com/user-attachments/assets/a8e67874-71f7-4c95-94ab-9aaf6d45c1b6)

(Query Result)







      

