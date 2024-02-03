# AdventureWorks OLTP Data Analysis
## Overview:
This documentation guides the process of extracting, modeling, and visualizing data from the AdventureWorks2019 OLTP database using Direct Query mode. The aim is to create a robust Power BI data model with a Star Schema for efficient analysis and then visualize the insights through an interactive Power BI report.

### 1. Data Extraction:
Data Source: [AdventureWorks OLTP Database](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver15&tabs=ssms).</br>
Tables to Extract:</br>
a. Sales.SalesOrderHeader </br>
b. Sales.SalesOrderDetail</br>
c. Sales.vSalesPerson (view)</br>
d. Sales.SalesTerritory</br>
e. Purchasing.ShipMethod</br>
f. Production.Product</br>
g. Production.ProductSubcategory</br>
h. Production.ProductCategory</br>
i. Status (Add based on ufnGetSalesOrderStatusText function)</br>
j. Dates (Power Query)</br>

### 2. Data Modeling:
Star Schema:
Design a Star Schema with a central fact table (e.g., SalesOrder) connected to dimension tables (e.g., Product, SalesPerson, Territory) through primary and foreign key relationships.
3. Data Refinement:
Table and Column Renaming:
Rename tables and columns for clarity and consistency.
Remove any unused columns to streamline the data model.
4. Measures:
# of Orders:

Calculation: Count of unique Sales Order IDs.
Total SubTotal Measure:

Calculation: Sum of the SubTotal for all sales orders.
Total Tax Measure:

Calculation: Sum of the Tax for all sales orders.
Total Freight Measure:

Calculation: Sum of the Freight for all sales orders.
Total Due Measure:

Calculation: Sum of the TotalDue for all sales orders.
Qty:

Calculation: Sum of the quantity of products in sales orders.
# Orders by OrderDate vs. ShipDate vs. DueDate:

Visualization Type: Line Chart
Description: Visualizes the number of orders over time based on Order Date, Ship Date, and Due Date.
# Orders by Status:

Visualization Type: Pie Chart
Description: Represents the distribution of orders based on their status.
# Orders by Shipmethod:

Visualization Type: Bar Chart
Description: Illustrates the number of orders using different ship methods.
# Orders by Category, Subcategory, Product:

Visualization Type: Treemap or Nested Bar Chart
Description: Hierarchically displays the breakdown of orders by product category, subcategory, and specific products.
# Orders by FlagOnlineOffline:

Visualization Type: Stacked Bar Chart
Description: Compares the number of online and offline orders.
# Orders and TotalDue by Territory:

Visualization Type: Dual-Axis Bar Chart or Map
Description: Provides a comparison of the number of orders and total due amount across different territories.
Top 10 Sales Persons (# Orders or Total Amount):

Visualization Type: Bar Chart
Description: Highlights the top 10 salespersons based on either the number of orders or total sales amount.
