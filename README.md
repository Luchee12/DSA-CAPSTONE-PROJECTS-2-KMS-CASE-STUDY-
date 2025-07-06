### DSA-CAPSTONE-PROJECTS-2-KMS-CASE-STUDY-

## WITH DATA PROVIDED I RAN ANALYSIS USING THE SQL QUERY

##### ANALYSIS OF KMS CASESTUDY
CREATE DATABASE KMS_DB

Create Table KMS_dbORDERS(
[Row_ID]INT,
[ORDER_ID]INT,
[ORDER_Date]Date,
[ORDER_Priority]varchar(50),
[ORDER_Quantity]Int,
Sales Decimal (10,2),
Discount Decimal (10,2),
[ship_Mode]Varchar (50),
Profit Decimal(10,2),
[Unit_Price]Decimal(10,2),
[Shipping_Cost]Decimal (10,2),
[Customer_Name] Varchar (255),
Province Varchar (100),
Region Nvarchar(100)
[Customer_segment] varchar (100),
[Product_Category]  varchar (100),
[product_sub_category]varchar (100),
[product_name]varchar (max),
[product_container] varchar(100),
[product_base margin] descimal(10,2)
[ship_date] date
)

---1

select product_category, sum([Sales]) as [Total sales]
from [dbo] .[KMS SQL case study]
group by product_category
order by [Total sales]desc

[dbo].[KMS SQL case study]
select * from [dbo].[KMS SQL case study]
CREATE DATABASE KULGAR_DB

----2

SELECT TOP 3 region,sum (sales) as [total sales]
from[dbo].[KMS SQL case study]
group by region
order by [total sales]desc


----3

select product_sub_category, sum(sales) as [total sales]
from  [dbo].[KMS SQL case study]
where region ='ontario'
group by product_sub_category


----4

select top 10 customer_Name, shipping_cost,sales, Discount, unit_price, sum(order_quantity) as [total order_quantity]
from[dbo].[KMS SQL case study]
group by customer_name,shipping_cost,sales,discount, unit_price
order by [total order_quantity]asc

----5

select Ship_mode, sum([shipping_cost]) as [total shipping_cost]
from [dbo].[KMS SQL case study]
group by ship_mode
order by [total shipping_cost]desc

----6

select customer_segment, product_sub_category,customer_name,sum(sales) as [Total sales]
from[dbo].[KMS SQL case study]
group by customer_segment, product_sub_category,customer_name
order by [total sales]desc


-----7

select top 1 *
from [dbo].[KMS SQL case study ]
where customer_segment ='small business'
order by sales desc

----8

select top 1*
from [dbo].[KMS SQL case study]
where customer_segment = 'corporate'
order by order_quantity desc

------9

select top 1*
from[dbo].[KMS SQL case study]
where customer_segment= 'consumer'
order by profit desc


-----10

select customer_name,customer_segment,product_category,product_sub_category
from[dbo].[KMS SQL case study]
join[dbo].[order_status]
on [dbo].[KMS SQL case study].order_ID=[dbo].[order_status].order_ID

-----11

SELECT 
"SHIP_MODE",
AVG("SHIPPING_COST") AS AVERAGESHIPPINGCOST
FROM 
[DBO].[KMS sql case study]
GROUP BY
"SHIP_MODE"
ORDER BY
AVERAGESHIPPINGCOST DESC;

 SELECT
 (ORDER_PRIORITY),
 (SHIP_MODE),
 COUNT(*)AS NUMBER_OF_ORDERS,
 SUM(SHIPPING_COST) AS
 TOTAL_SHIPPING_COST,
 AVG(SHIPPING_COST) AS AVG_SHIPPING
 FROM
 [KMS SQL CASE STUDY]
 GROUP BY
 (ORDER_PRIORITY),(SHIP_MODE)
ORDER BY
CASE (ORDER_PRIORITY)
WHEN 'CRITICAL' THEN 1
WHEN 'HIGH'  THEN 2
WHEN 'MEDIUM' THEN 3
WHEN 'LOW' THEN 4
ELSE 5
END,
SHIP_MODE;
 
