# AdventureWorks OLTP Data Analysis
## Overview:
This documentation guides the process of extracting, modeling, and visualizing data from the AdventureWorks2019 OLTP database using Direct Query mode. The aim is to create a robust Power BI data model with a Star Schema for efficient analysis and then visualize the insights through an interactive Power BI report.

![Sales Data Analysis](https://github.com/NouraAlgohary/AdventureWorks-OLTP-Data-Analysis/assets/103903785/f18ed6c3-66bb-4199-9c18-ae64d010e691)

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
- Star Schema: </br>
Designing a Star Schema with a central fact table (Fact|Order) connected to dimension tables (DIM|Salespersony, DIM|ShipMethod, DIM|Territory, DIM|Product) through primary and foreign key relationships.

![image](https://github.com/NouraAlgohary/AdventureWorks-OLTP-Data-Analysis/assets/103903785/f95266d6-dbc4-4114-8a82-8bf5151f86d5)

### 3. Data Refinement:
- Table and Column Renaming:</br>
- Renaming tables and columns for clarity and consistency.</br>
- Removing any unused columns to streamline the data model.</br>

### 4. Create DIM|Date using Power Query:
Date Dimension Creation:
- Using Power Query to create a Date dimension table (DIM|Date) based on the existing Dates table.
- Extracting relevant date-related information (Year, Month, Quarter, etc.) and adding calculated columns.
- Ensuring the Date dimension is properly linked to the central fact table using appropriate relationships.
```
Number.ToText(Date.Year([Date])) & 
(
    if Date.Month([Date]) < 10 then
        "0" & Number.ToText(Date.Month([Date]))
    else 
        Number.ToText(Date.Month([Date]))
) & 
(
    if Date.Day([Date]) < 10 then
        "0" & Number.ToText(Date.Day([Date]))
    else 
        Number.ToText(Date.Day([Date]))
)
```

### 4. Measures:
- No. of Orders:
Calculation: Count of unique Sales Order IDs.</br>

- Total SubTotal Measure:
Calculation: Sum of the SubTotal for all sales orders.</br>

- Total Tax Measure:
Calculation: Sum of the Tax for all sales orders.</br>

- Total Freight Measure:
Calculation: Sum of the Freight for all sales orders.</br>

- Total Due Measure:
Calculation: Sum of the TotalDue for all sales orders.</br>

- Qty:
Calculation: Sum of the quantity of products in sales orders.</br>

- No. of Orders by OrderDate vs. ShipDate vs. DueDate:
Visualization Type: Line Chart</br>
Description: Visualizes the number of orders over time based on Order Date, Ship Date, and Due Date.</br>

- No. of Orders by Status:
Visualization Type: Pie Chart</br>
Description: Represents the distribution of orders based on their status.</br>

- No. Orders by Shipmethod:
Visualization Type: Bar Chart</br>
Description: Illustrates the number of orders using different ship methods.</br>

- No. of Orders by Category, Subcategory, Product:
Visualization Type: Treemap or Nested Bar Chart</br>
Description: Hierarchically displays the breakdown of orders by product category, subcategory, and specific products.</br>

 - No. of Orders by FlagOnlineOffline:
Visualization Type: Stacked Bar Chart</br>
Description: Compares the number of online and offline orders.</br>

- No.of Orders and TotalDue by Territory:
Visualization Type: Dual-Axis Bar Chart or Map</br>
Description: Provides a comparison of the number of orders and total due amount across different territories.</br>

- Top 10 Sales Persons (No. of Orders or Total Amount):
Visualization Type: Bar Chart</br>
Description: Highlights the top 10 salespersons based on either the number of orders or total sales amount.</br>

### 5. Data Visualization and Power BI Report:
After modeling the data, proceed to create an interactive Power BI report incorporating the designed measures and visualizations. I used the Power BI platform to develop engaging dashboards and insightful reports that allow users to explore and understand the AdventureWorks OLTP data. Ensured proper use of colors, chart types, layout, and descriptive titles for a compelling and user-friendly experience.
