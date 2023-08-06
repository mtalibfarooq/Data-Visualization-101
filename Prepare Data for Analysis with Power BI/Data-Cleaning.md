# Get started with Power BI Desktop

In this task, you start by opening a starter Power BI (.pbix) file. The starter file doesn’t contain any data, but has been specially configured to help you complete the lab. The following report-level settings have been disabled in the starter file:

**Data Load > Import relationships from data sources on first load**
**Data Load > Autodetect new relationships after data is loaded**
Note: While having these two options enabled can be helpful when developing a data model, you disabled them earlier to support the lab experience. When you create relationships in the Load Data in Power BI Desktop lab, you’ll learn why you’re adding each one.

**Open Power BI Desktop.**

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image1.png)

Tip: By default, the Getting Started dialog box opens in front of Power BI Desktop. You can choose to sign-in, and then close the pop-up.

To open the starter Power BI Desktop file, select the **File > Open Report > Browse Reports**.

In the Open window, navigate to the **D:\PL300\Labs\01-prepare-data-with-power-query-in-power-bi-desktop\Starter** folder.

Select the **Sales Analysis file**.

Save a copy of the file with Save As in to the **D:\PL300\MySolution folder**.

## Get data from SQL Server

This task teaches you how to connect to a SQL Server database and import tables, which create queries in Power Query.

On the Home ribbon tab, from inside the Data group, select **SQL Server**.

![SQL Server Get Data icon](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image11.png)

In the SQL Server Database window, in the **Server** box, enter localhost, then select OK.

Note: In this lab, you’ll connect to the SQL Server database by using localhost because gateway data sources can’t resolve localhost. This isn’t a recommended practice when creating your own solutions.

If prompted for credentials, in the SQL Server Database window, select **Use my current credentials**, and then Connect.

In the Navigator window, at the left, expand the **AdventureWorksDW2020** database.

Note: The AdventureWorksDW2020 database is based on the AdventureWorksDW2017 sample database. It has been modified to support the learning objectives of the course labs.

Select—but don’t check—the **DimEmployee table**

![AdventureWorksDW2020 database with DimEmployee indicated](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image18.png)

In the right pane, notice a preview of the table data. The preview data allows you to see the columns and a sample of rows.

To create queries, select the checkbox next to the following six tables:

- DimEmployee
- DimEmployeeSalesTerritory
- DimProduct
- DimReseller
- DimSalesTerritory
- FactResellerSales

Complete this task by clicking **Transform Data**, which will open Power Query Editor.

This lab is only intended to connect to and profile the data, but not transform data.

## Preview Data in Power Query Editor

This task introduces the Power Query Editor and allows you to review and profile the data. This helps you determine how to clean and transform the data later.

In the Power Query Editor window, at the left, notice the **Queries pane**. The Queries pane contains one query for each table you checked.

![List of loaded queries](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image20.png)

Select the first query—**DimEmployee**.

The DimEmployee table in the SQL Server database stores one row for each employee. A subset of the rows from this table represents the salespeople, which will be relevant to the model you’ll develop.

At the bottom left corner of the status bar, some table statistics are provided—the table has 33 columns, and 296 rows.

![Count of 33 columns, 296 rows](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image22.png)

In the data preview pane, scroll horizontally to review all columns. Notice that the last five columns contain Table or Value links.

These five columns represent relationships to other tables in the database. They can be used to join tables together. You’ll join tables in the Load Data in Power BI Desktop lab.

To assess column quality, on the View ribbon tab, from inside the Data Preview group, check **Column Quality**. The column quality feature allows you to easily determine the percentage of valid, error, or empty values found in columns.

![Column Quality selection in ribbon](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image23.png)

Notice that the **Position** column has 94% empty (null) rows.

![Column quality showing 94% empty rows](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image24.png)

To assess column distribution, on the View ribbon tab, from inside the Data Preview group, check **Column Distribution**.

Review the Position column again, and notice that there are four distinct values, and one unique value.

Review the column distribution for the **EmployeeKey** column—there are 296 distinct values, and 296 unique values.

When the distinct and unique counts are the same, it means the column contains unique values. When modeling, it’s important that some model tables have unique columns. These unique columns can be used to create one-to-many relationships, which you’ll do in the Model Data in Power BI Desktop lab.

![Column distribution showing 296 distinct, 296 unique values](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image26.png)

In the Queries pane, select the **DimEmployeeSalesTerritory** query.

The DimEmployeeSalesTerritory table stores one row for each employee and the sales territory regions they manage. The table supports relating many regions to a single employee. Some employees manage one, two, or possibly more regions. When you model this data, you’ll need to define a many-to-many relationship.

In the Queries pane, select the **DimProduct** query. The DimProduct table contains one row per product sold by the company.

Horizontally scroll to reveal the last columns. Notice the **DimProductSubcategory** column.

When you add transformations to this query in the Load Data in Power BI Desktop lab, you’ll use the DimProductSubcategory column to join tables.

In the Queries pane, select the **DimReseller** query.

The DimReseller table contains one row per reseller. Resellers sell, distribute, or value add to the Adventure Works products.

To view column values, on the View ribbon tab, from inside the Data Preview group, check **Column Profile**.

Select the **BusinessType** column header, and notice the new pane beneath the data preview pane.

Review the column statistics and value distribution in the data preview pane.

Notice the data quality issue: there are two labels for warehouse (Warehouse, and the misspelled Ware House).

![Value distribution for the BusinessType column](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image31.png)

Hover the cursor over the **Ware House** bar, and notice that there are five rows with this value.

You’ll apply a transformation to relabel these five rows in the Load Data in Power BI Desktop lab.

In the Queries pane, select the **DimSalesTerritory** query.

The DimSalesTerritory table contains one row per sales region, including Corporate HQ (headquarters). Regions are assigned to a country, and countries are assigned to groups. In the Model Data in Power BI Desktop lab, you’ll create a hierarchy to support analysis at region, country, or group level.

In the Queries pane, select the **FactResellerSales** query.

The FactResellerSales table contains one row per sales order line—a sales order contains one or more line items.

Review the column quality for the **TotalProductCost** column, and notice that 8% of the rows are empty.

Missing TotalProductCost column values is a data quality issue. To address the issue, in the Load Data in Power BI Desktop lab, you’ll apply transformations to fill in missing values by using the product standard cost, which is stored in the related DimProduct table.

## Get data from a CSV file

In this task, you’ll create a new query based on CSV files.

To add a new query, in the Power Query Editor window, on the Home ribbon tab, from inside the New Query group, select the New Source down-arrow, and then select **Text/CSV**.

In the Open window, navigate to the **D:\PL300\Resources** folder, and select the **ResellerSalesTargets.csv** file. Select **Open**.

In the **ResellerSalesTargets.csv** window, review the preview data. Select **OK**.

In the Queries pane, notice the addition of the **ResellerSalesTargets** query.

The ResellerSalesTargets CSV file contains one row per salesperson, per year. Each row records 12 monthly sales targets (expressed in thousands). The business year for the Adventure Works company commences on July 1.

Notice that no column contains empty values. When there isn’t a monthly sales target, a hyphen character is stored instead.

Review the icons in each column header, to the left of the column name. The icons represent the column data type. 123 is a whole number, and ABC is text.

![Picture 74](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image38.png)

Repeat the steps to create a query based on the **D:\PL300\Resources\ColorFormats.csv** file.

The ColorFormats CSV file contains one row per product color. Each row records the HEX codes to format background and font colors.

You should now have two new queries, **ResellerSalesTargets** and **ColorFormats**.

![Queries list](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-all-queries-loaded.png)

## Finish up

In this task, you’ll complete the lab.

On the View ribbon tab, from inside the Data Preview group, uncheck the three data preview options that were previously enabled in this lab:

- Column quality
- Column distribution
- Column profile

![Picture 76](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image40.png)

Save the Power BI Desktop file. When prompted to apply the pending changes, select **Apply Later**.

Tip: Applying the queries will load their data into the data model. You’re not ready to do that, as there are many transformations that must be applied first.
Note: Replace image_url_here with the actual URLs of the images you want to insert.







