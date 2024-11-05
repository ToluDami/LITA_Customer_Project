# LITA_Customer_Project

This is where I documented the second project I submitted while learning at Incubator Hub. This project involves analyzing customer data for a subscription service to identify segments and trends. My goal is to understand customer behavior, track subscription types, and identify key trends in cancelations and renewals.

## Data Description
The dataset includes the following fields:
- Customer ID
- Customer Name
- Region
- Subscription Type
- Subscription Start
- Subscription End
- Cancelled
- Revenue
- Subscription Duration

## Basic Statistics about the dataset:
- Total Number of Customers - 33787
- 3 subscription types
- 4 Regions
- Average subscription Duration of 365days
- Total Revenue - 67,540,175

## Data Manipulation

### Data Cleaning
The data had to be cleaned to remove duplicates and blank cells.

## Tools Used
- Microsoft Excel
- Microsoft SQL
- Microsoft Power BI
  
### Microsoft Excel for Data Analysis and Visualisation

![image](https://github.com/user-attachments/assets/4b1e412b-65c1-4cb7-a431-b9c6b1852ed1)

### Microsoft SQL For Querying of Data
SQL was used to answer various questions as can be seen in the queries below

```select * from [dbo].[LITA Capstone Customer_Dataset]

-----retrieve the total number of customers from each region-----
Select  region, count(distinct Customerid) as total_customers 
from [dbo].[LITA Capstone Customer_Dataset]
Group by region;

------find the most popular subscription type by the number of customers-----
Select top 1 subscriptiontype, count(distinct customerid) as total_customers
From [dbo].[LITA Capstone Customer_Dataset]
Group by subscriptiontype 
Order by total_customers desc;

-----find customers who canceled their subscription within 6 months-----
SELECT CustomerID, CustomerName, SubscriptionStart, SubscriptionEnd,canceled
from [dbo].[LITA Capstone Customer_Dataset]
where canceled = 1
and datediff(month, subscriptionEnd,
SubscriptionStart) <= 6

-----calculate the average subscription duration for all customers----
Select avg(datediff(day, subscriptionstart, subscriptionend)) as avg_subscription_duration
From [dbo].[LITA Capstone Customer_Dataset]

----find customers with subscriptions longer than 12 months----
Select customerid as longsubscription
From [dbo].[LITA Capstone Customer_Dataset]
Where datediff(month, subscriptionstart, subscriptionend) > 12
group by CustomerID;

----calculate total revenue by subscription type-----
Select subscriptiontype,
Sum(revenue) as total_revenue 
From [dbo].[LITA Capstone Customer_Dataset]
Group by subscriptiontype;

-----find the top 3 regions by subscription cancellations----
Select top 3 region,
Count(CustomerID) as Cancelation_Count
From [dbo].[LITA Capstone Customer_Dataset]
Where Canceled = 1
Group by region
Order by Cancelation_Count desc;

-----find the total number of active and canceled subscriptions-----
SELECT 
  SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
  SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM [dbo].[LITA Capstone Customer_Dataset]
```

![image](https://github.com/user-attachments/assets/672bd3eb-a531-4581-ab21-7e0f9998517d)

![image](https://github.com/user-attachments/assets/d9c25786-143d-447d-a5ec-06fb3f1f37c8)

![image](https://github.com/user-attachments/assets/1001ff35-1fe9-45ca-a552-18404081e7f3)

![image](https://github.com/user-attachments/assets/6c19d9bc-abb4-473b-a0d5-2fab27105959)

![image](https://github.com/user-attachments/assets/b6b21013-4c41-455b-9b10-0880e201410c)

![image](https://github.com/user-attachments/assets/3f591029-af85-4ebf-8f88-0a921c637d5f)

![image](https://github.com/user-attachments/assets/9d49393a-3b52-40af-8afc-84eaaf41b295)

![image](https://github.com/user-attachments/assets/2fb1c722-0a32-4ad4-890f-010b50d7886a)

![image](https://github.com/user-attachments/assets/72afbc1b-f01f-4dfa-a6c7-360babf12abc)

### Microsoft Power BI
This was used for data cleaning as well as visualisations
![image](https://github.com/user-attachments/assets/893c8d89-a63b-4a18-849d-39190d46e8d9)

![image](https://github.com/user-attachments/assets/54806b10-d02d-4fa1-8b2b-c508120a157d)

![image](https://github.com/user-attachments/assets/946ea5eb-fa0e-4a42-8c8e-1be59319436c)







