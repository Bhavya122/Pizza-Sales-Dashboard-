PIZZA REPORT PROJECT

1. SELECT SUM(total_price) AS total_price_sum

FROM pizza_sales;

- total_price_

817860.05083847

**2\.** SELECT SUM (total_price)/ COUNT (DISTINCT order_id) AS avg_order_value

from pizza_sales

**\= 38.3072623343546**

**3** SELECT SUM (quantity) as total_pizza_sold from pizza_sales

\= 49574

4\. select count (distinct order_id) as total_orders from pizza_sales

\= 21350

5\. select cast (cast (sum(quantity)as decimal(10,2) )/

cast(count (distinct order_id) as decimal(10,2)) as decimal (10,2) )from pizza_sales

\=2 .32

6\. select datename (dw,order_date) as order_day ,count (distinct order_id) as total_order from pizza_sales

group by DATENAME (dw, order_date)

order_day total_order

\=Saturday 3158

Wednesday 3024

Monday 2794

Sunday 2624

Friday 3538

Thursday 3239

Tuesday 2973

7\. select datename (month , order_date) as month_name , count (distinct order_id) as total_orders

from pizza_sales

group by DATENAME (month , order_date)

order by total_orders desc

\=month_name total_orders

July 1935

May 1853

January 1845

August 1841

March 1840

April 1799

November 1792

June 1773

February 1685

December 1680

September 1661

October 1646

8\. select pizza_category, sum (total_price)as total_sales , sum (total_price)\*100/(select sum(total_price) from pizza_sales)as pct

from pizza_sales

group by pizza_category

\=pizza_category total_sales pct

Classic 220053.100021362 26.9059602306976

Chicken 195919.5 23.9551375322885

Veggie 193690.451004028 23.6825910258677

Supreme 208196.99981308 25.4563112111462

9\. select pizza_category, sum (total_price)as total_sales , sum (total_price)\*100/(select sum(total_price) from pizza_sales where month (order_date)=1)as pct

from pizza_sales

where month (order_date)=1 // this means (1= jan month )here(no =month ) for data of particular month

group by pizza_category

\=pizza_category total_sales pct

Classic 18619.4000015259 2.27659976574687

Chicken 16188.75 1.97940344236196

Veggie 17055.4000778198 2.0853690139694

Supreme 17929.7499866486 2.19227604628285

10\. USE pizza_db

select \* from pizza_sales

select pizza_size, cast(sum (total_price) as decimal(10,2))as total_sales , cast (sum (total_price)\*100/(select sum(total_price) from pizza_sales)as decimal(10,2))as pct

from pizza_sales

group by pizza_size

order by pct desc

\= pizza_size total_sales pct

L 375318.701004028 45.8903330244889

M 249382.25 30.492044420599

S 178076.49981308 21.7734684107037

XL 14076 1.72107684995364

XXL 1006.6000213623 0.123077294254725
