# LITA-Capstone-Project-2
Project 2 of the Capstone project

## Excel



## SQL

```SQL
select * from Capstone_CustomerData
```

 --- retrieve the total number of customers from each region ---

 ```SQL
select count(distinct customerid) as number_customers, region
 from Capstone_CustomerData
 group by region
```

 --- find the most popular subscription type by the number of customers. ---
 
 ```SQL
 create view view_two as
 (select (count(distinct customerid)) as number_sub, SubscriptionType
 from Capstone_CustomerData
 group by SubscriptionType)
```

 ```SQL
select top 1* from view_two
```

 --- find customers who canceled their subscription within 6 months  ---

```SQL
select CustomerID, customername
 from Capstone_CustomerData
 where DATEDIFF(month, subscriptionstart, subscriptionend) <=6
```
 

> calculate the average subscription duration for all customers ---

```SQL
select AVG(DATEDIFF(month, subscriptionstart, subscriptionend))
as average_subs_duration
from Capstone_CustomerData
```

> find customers with subscriptions longer than 12 months ---

```SQL
 select CustomerID, customername
 from Capstone_CustomerData
 where DATEDIFF(month, subscriptionstart, subscriptionend) >12
```

> calculate total revenue by subscription type. ---

 ```SQL
 select sum(revenue) as revenue_per_substype, SubscriptionType
 from Capstone_CustomerData
 group by SubscriptionType
``

 > find the top 3 regions by subscription cancellations. ---

```SQL
 select top 3 count(distinct customerid) nb_cancel, region
 from Capstone_CustomerData
 where canceled='vrai'
 group by Region
 order by nb_cancel desc
```

 > find the total number of active and canceled subscriptions. ---

 select count(distinct customerid) nb_active
 from Capstone_CustomerData
 where canceled = 'faux'

 select count(distinct customerid) nb_canceled
 from Capstone_CustomerData
 where canceled = 'vrai'

## Power Bi
