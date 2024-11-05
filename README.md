# Capstone Project 2

# Project Title: Customer Segmentation for a Subscription Service

## Project Overview
This Data Analysis Project involves analyzing customer data for a subscription service to identify segments and trends. By exploring the customer data and analysing the various parameters, I seek to understand customer behaviour, track subscription types and identify key trends in cancellations and renewals. This would help make data-driven decisions and enable me tell a unique story with the insights gotten from the data.

## Table of Content
* *Project Title*
* *Project Overview*
* *Data Sources*
* *Tools Used*
* *Data Cleaning and Preparation*
* *Exploratory Data Analysis*
* *Data Analysis*
* *Data Visualization*
* *Recommendations*
  
### Data Sources
The primary source of Data used in this Project is Sales Data file and this can be downloaded here[Sales Data.csv](https://github.com/user-attachments/files/17631070/Sales.Data.csv)


### Tools Used
- Microsoft Excel for Data Cleaning [Download Here](https://www.microsoft.com)
- SQL Server for Querying and Analysis [Download Here](https://www.microsoft.com)
- Microsoft Power BI for  Analysis and Visualiation [Download Here](https://www.microsoft.com)
- Github for Portfolio building [Download Here](https://www.github.com)

### Data Cleaning and Preparation
**Steps Taken:**

1. **Import Data:**
   - The customer dataset was imported into Excel for initial exploration and cleaning.

2. **Remove Duplicates:**
   - Ensured the dataset was free of duplicate records by removing any duplicates based on `CustomerID`.

3. **Handle Missing Values:**
   - Checked for and addressed any missing values within the dataset.

4. **Standardize Data:**
   - Ensured consistent formatting of text data, such as converting all text to uppercase where necessary.

5. **Create New Columns:**
   - **Subscription Duration**: Derived in months using `(SubscriptionEnd - SubscriptionStart) / 30`.

### Data Analysis in Excel 
**Pivot Tables:**

1. **Subscription Patterns:**
   - Created pivot tables to analyze count of subscription type by `Region`.
    ![Screenshot 2024-11-04 145427](https://github.com/user-attachments/assets/3b268996-dac1-444d-9232-5142be1c3f2f)

   - Created pivot tables to analyze Total Revenue by `SubscriptionType` and `Region`.
![Screenshot 2024-11-04 145534](https://github.com/user-attachments/assets/0c40377a-3a76-44bb-b0e8-cf14966c02a1)


2. **Subscription Duration:**
   - Calculated the average subscription duration using the formula `=AVERAGE(DurationMonths)`.
   - ![Screenshot 2024-11-05 113650](https://github.com/user-attachments/assets/25ee2922-3a98-4180-9073-9ced65f1b6fc)


3. **Popular Subscription Types:**
   - Created pivot tables to determine the count of customers by `SubscriptionType`.
     ![Screenshot 2024-11-04 145353](https://github.com/user-attachments/assets/bb617462-a55d-4d50-8efd-d8ee2e038dac)


4.  **Total Revenue by Subscription Type:**
   - Created pivot tables to summarize total revenue by `SubscriptionType`.
     ![Screenshot 2024-11-04 145317](https://github.com/user-attachments/assets/c0b80af3-11aa-43ca-a7c3-b287acc8546c)


 5. **Cancellations by Region and Subscription Type:**
   - Created pivot tables to summarize cancellations by `Region` and `SubscriptionType`.
     ![Screenshot 2024-11-04 145203](https://github.com/user-attachments/assets/ca04af40-7e37-4689-bc0d-d92b82b7f536)


### SQL Analysis
SQL Analysis

**Queries Executed:**

1. **Total Number of Customers from Each Region:**
   ```sql
   SELECT Region, COUNT(CustomerID) AS TotalCustomers
   FROM CustomerData
   GROUP BY Region;
   ```
   ![Screenshot 2024-11-05 095334](https://github.com/user-attachments/assets/9c966176-1b71-4ae0-832a-2bdaacc6b28a)


2. **Most Popular Subscription Type:**
   ```sql
   SELECT SubscriptionType, COUNT(CustomerID) AS NumberOfCustomers
   FROM CustomerData
   GROUP BY SubscriptionType
   ORDER BY NumberOfCustomers DESC;
   ```
   ![Screenshot 2024-11-05 095711](https://github.com/user-attachments/assets/dd974093-4aaf-44a0-b90c-63095d5099cd)


3. **Customers Who Canceled Within 6 Months:**
   ```sql
   SELECT CustomerID, CustomerName
   FROM CustomerData
   WHERE Canceled = 1 AND DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6;
   ```
   ![Screenshot 2024-11-05 100814](https://github.com/user-attachments/assets/65e7a1f3-d065-437f-a849-54507219af3a)


4. **Average Subscription Duration:**
   ```sql
   SELECT AVG(DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd)) AS AvgDuration
   FROM CustomerData;
   ```
   ![Screenshot 2024-11-05 100756](https://github.com/user-attachments/assets/831a297b-4296-4af3-aabd-5ac4d43fd7c9)


5. **Customers with Subscriptions Longer Than 12 Months:**
   ```sql
   SELECT CustomerID, CustomerName
   FROM CustomerData
   WHERE DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) > 12;
   ```
   ![Screenshot 2024-11-05 100716](https://github.com/user-attachments/assets/62183759-597c-49d5-a4e6-b42c1618bc7a)


6. **Total Revenue by Subscription Type:**
   ```sql
   SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
   FROM CustomerData
   GROUP BY SubscriptionType;
   ```
   ![Screenshot 2024-11-05 100701](https://github.com/user-attachments/assets/be5cd1e6-10b4-4b2a-a82a-9d609f200a0f)


7. **Top 3 Regions by Subscription Cancellations:**
   ```sql
   SELECT Region, COUNT(CustomerID) AS Cancellations
   FROM CustomerData
   WHERE Canceled = 1
   GROUP BY Region
   ORDER BY Cancellations DESC
   LIMIT 3;
   ```
   ![Screenshot 2024-11-05 101216](https://github.com/user-attachments/assets/606fc36e-bae8-406e-a28c-a242ed677ae8)


8. **Total Number of Active and Canceled Subscriptions:**
   ```sql
   SELECT Canceled, COUNT(CustomerID) AS TotalSubscriptions
   FROM CustomerData
   GROUP BY Canceled;
   ```
   ![Screenshot 2024-11-05 101437](https://github.com/user-attachments/assets/5323d284-07d9-4528-9593-2b63513c9399)

   ### Power BI Dashboard

**Steps Taken:**

1. **Load Data into Power BI:**
   - Imported the cleaned and prepared dataset into Power BI Desktop.

2. **Create Visuals:**
   - **Customer Segments:**
     - Bar chart showing the number of customers by subscription type.
   - **Cancellations:**
     - Map or bar chart showing the number of cancellations by region.
   - **Subscription Trends:**
     - Line chart showing the number of active and canceled subscriptions over time.
   - **Revenue Analysis:**
     - Pie chart or bar chart showing total revenue by subscription type.

3. **Add Slicers:**
   - Added slicers for `Region`, `SubscriptionType`, and `Canceled` to allow for interactive data exploration.

4. **Design and Layout:**
   - Arranged the visuals in a logical and visually appealing layout.
   - Used appropriate colors and themes to enhance readability.

5. **Publish Dashboard:**
   - Published the Power BI dashboard to the Power BI service for sharing and collaboration.




