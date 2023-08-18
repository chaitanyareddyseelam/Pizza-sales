# Pizza-sales
Analysis of pizza sales throughout a calendar year using several criteria
*1.Total Revenue*/
 select sum(total_price) as Revenue from pizza_sales
 
 /*2.Average Order value*/
 select sum(total_price)/count( distinct order_id) as Avgerage_order_value from pizza_sales
 
 /*3.Total pizzas sold*/
 select sum(quantity) as Total_pizzas_sold from pizza_sales
 
 /*4.Total orders*/
 select count( distinct order_id) as Total_orders from pizza_sales
 
 /*5.Avereage pizzas per order*/
 select count(pizza_id)/count( distinct order_id) as Avgerage_o from pizza_sales
 
 /*6.Daily Trend for Total Orders*/
 
 select datename(weekday, order_date) as
 Order_day,count(distinct order_id) 
 as order_count from pizza_sales 
 group by datename(weekday, order_date)
 order by Order_day
 
 /*7.Monthly Trend for Orders*/
 
 select datename(month, order_date) as
 Order_day,count(distinct order_id) 
 as order_count from pizza_sales 
 group by datename(month, order_date);
 
 /*8.percantage of sales by each category*/
 
 select Pizza_category,sum(total_price) as revenue,
sum(total_price)*100/(select sum(total_price) from pizza_sales) as percentage
 from pizza_sales group by Pizza_category;
 
 /*9.percantage of sales by each category*/
 
 select Pizza_size,sum(total_price) as revenue,
sum(total_price)*100/(select sum(total_price) from pizza_sales) as percentage
 from pizza_sales group by Pizza_size;
 
 /*10.total pizzas sold by pizza category*/
 select pizza_category ,sum(quantity) as total_pizza from pizza_sales group by pizza_category
 
 /*11.top 5 pizzas by revenue*/
 select top 5 pizza_name,sum(total_price) as Revenue from pizza_sales
 group by Pizza_name
 order by Revenue desc
 
 /*12.Bottom 5 Pizzas by Revenue*/
 select top 5 pizza_name,sum(total_price) as Revenue from pizza_sales
 group by Pizza_name
 order by Revenue asc 
 
 /*13.Top 5 Pizzas by Quantity*/
 select top 5 pizza_name,count(quantity) as Quantity from pizza_sales
 group by Pizza_name
 order by Quantity desc
 
 /*14.Top 5 Pizzas by Total Orders*/
 select top 5 pizza_name,count(distinct order_id) as total_orders from pizza_sales
 group by Pizza_name
 order by total_orders desc






 
