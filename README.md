# Pizza Sales Report-Dashboard

### Dashboard Link : https://app.powerbi.com/links/pT_698_4LT?ctid=d4963ce2-af94-4122-95a9-644e8b01624d&pbi_source=linkShare

## Problem Statement
 
This dashboard assists the pizza business in understanding its sales performance through various metrics and trends. It enables the business to identify areas for improvement and make data-driven decisions to enhance overall performance. By analyzing key performance indicators (KPIs) such as total revenue, average order value, total pizzas sold, and total orders, the business can gain insights into its financial health and operational efficiency. Additionally, the dashboard provides detailed trends on daily and monthly orders, sales by pizza category and size, and the performance of specific pizzas by revenue and quantity sold. This comprehensive analysis empowers the business to optimize its operations, improve customer satisfaction, and increase profitability. 

### Steps followed 
Step 1: Load Data into Power BI
Open Power BI Desktop.
Load your data:
Go to Home > Get Data.
Select the appropriate data source (e.g., SQL Server, CSV file, etc.).
Load the pizza_sales data into Power BI.

Step 2: Create and Execute SQL Queries
Open Power Query Editor:
Go to Home > Transform Data.
Run the SQL Queries to prepare data for visualization:
Total Revenue- SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
(https://github.com/nirabhi18/test/assets/174709222/9c4cd00d-9cab-4b78-89ee-4d2cb94608a8) 
Average Order Value-SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales;
(https://github.com/nirabhi18/test/assets/174709222/5abcbbfd-04e3-470c-b94f-eef2adea29f1) 
Total Pizzas Sold- SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales;
(https://github.com/nirabhi18/test/assets/174709222/9d6d8b03-d21f-40dd-a1cb-8dfbd1936dc5) 
Total Orders- SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales;
(https://github.com/nirabhi18/test/assets/174709222/20198b9c-c798-4b80-884b-5edfaee81999) 
Average Pizzas Per Order- SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2)) AS Avg_Pizzas_per_order FROM pizza_sales;
(https://github.com/nirabhi18/test/assets/174709222/5b9f4f69-1eb6-45e3-af91-c3714ecbb913) 
Daily Trend for Total Orders- SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders FROM pizza_sales GROUP BY DATENAME(DW, order_date);
(https://github.com/nirabhi18/test/assets/174709222/fc72b18a-2bfc-4d2a-be69-3d3fdbd6113a) 
Monthly Trend for Orders- SELECT DATENAME(MONTH, order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY DATENAME(MONTH, order_date);
(https://github.com/nirabhi18/test/assets/174709222/cc8556b4-ebbc-4722-a748-9109718ef206) 
% of Sales by Pizza Category-SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_category;
(https://github.com/nirabhi18/test/assets/174709222/8a4cb77f-a08d-4403-8761-6a3a63f121e4) 
% of Sales by Pizza Size- SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue, CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) FROM pizza_sales) AS DECIMAL(10,2)) AS PCT FROM pizza_sales GROUP BY pizza_size ORDER BY pizza_size;
(https://github.com/nirabhi18/test/assets/174709222/ea151635-7973-476d-b3e8-fef4bdd5b6a6) 
Total Pizzas Sold by Pizza Category- SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold FROM pizza_sales WHERE MONTH(order_date) = 2 GROUP BY pizza_category ORDER BY Total_Quantity_Sold DESC;
(https://github.com/nirabhi18/test/assets/174709222/98effba5-bfdf-449b-8d82-0b52b01d9efc) 
Top 5 Pizzas by Revenue- SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue DESC;
(https://github.com/nirabhi18/test/assets/174709222/65cb52b9-8dfa-420a-a589-db8e1d8c9a0f) 
Bottom 5 Pizzas by Revenue- SELECT TOP 5 pizza_name, SUM(total_price) AS Total_Revenue FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Revenue ASC;
(https://github.com/nirabhi18/test/assets/174709222/3e68fc27-15b6-41c9-b981-bca4da510d15)
Top 5 Pizzas by Quantity- SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Pizza_Sold DESC;
(https://github.com/nirabhi18/test/assets/174709222/837d9ce7-c98b-4939-a87a-c316d6a169c3) 
Bottom 5 Pizzas by Quantity-SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Pizza_Sold ASC;
(https://github.com/nirabhi18/test/assets/174709222/7e4a6dd8-6014-4087-9eb3-8164eba240aa) 
Top 5 Pizzas by Total Orders:SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Orders DESC;
(https://github.com/nirabhi18/test/assets/174709222/bb963ca5-8115-4486-9b4d-cb7d1547cde6) 
Bottom 5 Pizzas by Total Orders- SELECT TOP 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales GROUP BY pizza_name ORDER BY Total_Orders ASC;
(https://github.com/nirabhi18/test/assets/174709222/050e2025-8b93-4909-9bcf-5d3c9e433695)

Step 3: Transform and Clean Data
Ensure data is clean:
Remove duplicates, handle missing values, and ensure data types are correct.
Apply necessary transformations using Power Query Editor.
Step 4: Create Visuals in Power BI Report
Create Visualizations:

Total Revenue: Use a Card visual to display the total revenue.
Average Order Value: Use a Card visual for the average order value.
Total Pizzas Sold: Use a Card visual for the total pizzas sold.
Total Orders: Use a Card visual for the total orders.
Average Pizzas Per Order: Use a Card visual for the average pizzas per order.
Daily Trend for Total Orders: Use a Line Chart or Bar Chart to show the trend.
Monthly Trend for Orders: Use a Line Chart or Bar Chart for monthly trends.
% of Sales by Pizza Category: Use a Pie Chart or Donut Chart for percentage distribution.
% of Sales by Pizza Size: Use a Pie Chart or Donut Chart for percentage distribution.
Total Pizzas Sold by Pizza Category: Use a Bar Chart to show quantities sold by category.
Top 5 and Bottom 5 Pizzas by Revenue: Use Bar Charts to show the top and bottom performers.
Top 5 and Bottom 5 Pizzas by Quantity: Use Bar Charts to show the top and bottom performers by quantity.
Top 5 and Bottom 5 Pizzas by Total Orders: Use Bar Charts to show the top and bottom performers by total orders.
Add Slicers for Interactivity:

Add slicers for Pizza Type, Customer Type, Location, and Order Type to allow users to filter data dynamically.
Step 5: Design and Format the Report
Customize the Theme:
Go to View > Themes and choose a theme or create a custom theme.
Add Titles and Labels:
Use text boxes to add report titles, section headers, and labels to visuals.
Add Company Branding:
Insert the company's logo and other branding elements using the Insert tab.
Optimize Layout:
Arrange visuals logically and ensure the layout is clean and easy to navigate.
Step 6: Publish and Share the Report
Save the Report.
Publish to Power BI Service:
Go to Home > Publish and select your workspace.
      

 # Report Snapshot (Power BI DESKTOP)

 
![Dashboard_upload] 
![pizzareport1](https://github.com/nirabhi18/test/assets/174709222/2437db11-5b6b-4c70-84bd-c24a3a3771a7) 

![pizzareport2](https://github.com/nirabhi18/test/assets/174709222/12eeb436-6663-4c74-99ca-79d7b41cebd9)


# Insights

A two page report was created on Power BI Desktop & it was then published to Power BI Service.

Key Performance Indicators (KPIs)
[1] Total Orders = 21,350
Insight: This represents the total number of distinct orders placed by customers.
[2] Total Pizzas Sold= 49,574
Insight: The total number of pizzas sold.
[3] Total Revenue= $817.86K
Insight: This represents the total revenue generated from all pizza sales.
[4] Average Order Value= $38.31
Insight: The average value of each order placed.
[5] Average Pizzas Per Order= 2.32
Insight: The average number of pizzas ordered per order.

Best Sellers
[6] Revenue
Top Contributor: The Thai Chicken Pizza contributes to maximum revenue.
[7] Quantity
Top Contributor: The Classic Deluxe Pizza contributes to maximum total quantities.
[8] Total Orders
Top Contributor: The Classic Deluxe Pizza contributes to maximum total orders.

Worst Sellers
[9] Revenue
Lowest Contributor: The Brie Carre Pizza contributes to minimum revenue.
[10] Quantity
Lowest Contributor: The Brie Carre Pizza contributes to minimum total quantities.
[11] Total Orders
Lowest Contributor: The Brie Carre Pizza contributes to minimum total orders.

Top 5 Pizzas by Revenue

The Thai Chicken Pizza: $43K
The Barbecue Chicken Pizza: $41K
The Californian Pizza: $41K
The Classic Deluxe Pizza: $38K
The Spicy Italian Pizza: $35K

Top 5 Pizzas by Quantity

The Classic Deluxe Pizza: 2.5K
The Barbecue Chicken Pizza: 2.4K
The Hawaiian Pizza: 2.4K
The Pepperoni Pizza: 2.4K
The Thai Chicken Pizza: 2.4K

Bottom 5 Pizzas by Revenue

The Spinach Pizza: $16K
The Mediterranean Pizza: $15K
The Spicy Italian Pizza: $15K
The Green Garden Pizza: $14K
The Brie Carre Pizza: $12K

Bottom 5 Pizzas by Quantity

The Soppressata Pizza: 961
The Spinach Pizza: 950
The Calabrese Pizza: 937
The Mediterranean Pizza: 934
The Brie Carre Pizza: 490

Bottom 5 Pizzas by Total Orders

The Chicken Caesar Pizza: 938
The Calabrese Pizza: 918
The Spinach Pizza: 918
The Mediterranean Pizza: 912
The Brie Carre Pizza: 480
