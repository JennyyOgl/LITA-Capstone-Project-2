# LITA Capstone Project 2
Project 2 of the Capstone project

## Excel
- Analyze customer data using pivot tables to find subscription patterns.

 ![Pivot table 2](https://github.com/user-attachments/assets/518d3927-45d7-419c-a167-3e2cbc1b7a8d)


- Calculate the average subscription duration and identify the most popular subscription types.

  ![Average subscription duration](https://github.com/user-attachments/assets/6d9a0c88-b959-4545-86e4-12098987159a)


- Create any other interesting report.


## SQL

```SQL
select * from Capstone_CustomerData
```

> retrieve the total number of customers from each region ---

 ```SQL
select count(distinct customerid) as number_customers, region
 from Capstone_CustomerData
 group by region
```

> find the most popular subscription type by the number of customers. ---
 
 ```SQL
 create view view_two as
 (select (count(distinct customerid)) as number_sub, SubscriptionType
 from Capstone_CustomerData
 group by SubscriptionType)
```

 ```SQL
select top 1* from view_two
```

> find customers who canceled their subscription within 6 months  

```SQL
select CustomerID, customername
 from Capstone_CustomerData
 where DATEDIFF(month, subscriptionstart, subscriptionend) <=6
```
 

> calculate the average subscription duration for all customers 

```SQL
select AVG(DATEDIFF(month, subscriptionstart, subscriptionend))
as average_subs_duration
from Capstone_CustomerData
```

> find customers with subscriptions longer than 12 months 

```SQL
 select CustomerID, customername
 from Capstone_CustomerData
 where DATEDIFF(month, subscriptionstart, subscriptionend) >12
```

> calculate total revenue by subscription type. 

 ```SQL
 select sum(revenue) as revenue_per_substype, SubscriptionType
 from Capstone_CustomerData
 group by SubscriptionType
```

 > find the top 3 regions by subscription cancellations. 

```SQL
 select top 3 count(distinct customerid) nb_cancel, region
 from Capstone_CustomerData
 where canceled='vrai'
 group by Region
 order by nb_cancel desc
```

 > find the total number of active and canceled subscriptions. ---

``` SQL
 select count(distinct customerid) nb_active
 from Capstone_CustomerData
 where canceled = 'faux'
```
``` SQL
 select count(distinct customerid) nb_canceled
 from Capstone_CustomerData
 where canceled = 'vrai'
```

## Power Bi
![Number of cancellations per month](https://github.com/user-attachments/assets/f88f6bd5-d04e-4901-8045-154694f8a51a)

![Cancellation overview](https://github.com/user-attachments/assets/7b4a698d-c463-4794-b1c6-3c667f809953)



