
## Get started
In this task, you’ll set up the environment for the lab.

Open Power BI Desktop.

Power BI Desktop icon


1. ![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image1.png)

Tip: By default, the Getting Started dialog box opens in front of Power BI Desktop. You can choose to sign-in, and then close the pop-up.

2. To open the starter Power BI Desktop file, select the File > Open Report > Browse Reports.

3. Navigate to the D:\PL300\Labs\03-configure-data-model-in-power-bi-desktop\Starter folder and select the Sales Analysis file.

4. Close any informational windows that may open.

5. Go to File > Save As and save the file to the D:\PL300\MySolution folder.

## Create model relationships
In this task, you’ll create model relationships. The file was configured to not identify relationships between tables in the previous labs. This isn’t the default setting, but is recommended to prevent extra work creating the correct relationships for your model.

Important: The labs use a shorthand notation to reference a field. It will look like this: Product | Category. In this example, Product is the table name and Category is the field name.

1. In Power BI Desktop, at the left, select the Model view icon.


![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image9.png)


2. If you don’t see all seven tables, scroll horizontally to the right, and then drag and arrange the tables more closely together so they can all be seen at the same time.

Tip: You can also use the zoom control located at the bottom of the window.

3. To return to Report view, at the left, select the Report view icon.


![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image10.png)


4. To view all table fields, in the Data pane, right-click an empty area, and then select Expand All.

5. To create a table visual, in the Data pane, from inside the Product table, check the Category field.

6. To add another column to the table, in the Data pane, check the Sales | Sales field.

7. Notice that the table visual lists four product categories, and that the sales value is the same for each, and the same for the total.

The issue is that the table is based on fields from different tables. The expectation is that each product category displays the sales for that category. However, because there isn’t a model relationship between these tables, the Sales table isn’t filtered. You’ll now add a relationship to propagate filters between the tables.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image10.png)

8. On the Modeling ribbon tab, from inside the Relationships group, select Manage Relationships.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image14.png)

9. In the Manage Relationships window, notice that no relationships are yet defined.

10. To create a relationship, select New.

11. In the Create Relationship window, in the first dropdown list, select the Product table.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image16.png)

12. In the second dropdown list (beneath the Product table grid), select the Sales table.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image17.png)

13. Notice the ProductKey columns in each table have been automatically selected.
     The columns were selected because they share the same name and data type. You may need to find matching columns with different names in real data.

14. In the Cardinality dropdown list, notice that One To Many (1:*) is selected.

 The cardinality was automatically detected, because Power BI understands that the ProductKey column from the Product table contains unique values. One-to-many relationships are the most common cardinality, and all relationship you create in this lab will be this type.

15. In the Cross Filter Direction dropdown list, notice that Single is selected.

 Single filter direction means that filters propagate from the “one side” to the “many side”. In this case, it means filters applied to the Product table will propagate to the Sales table, but not in the opposite direction.

16. Notice that the Mark This Relationship Active is checked.

Active relationships propagate filters. It’s possible to mark a relationship as inactive so filters don’t propagate. Inactive relationships can exist when there are multiple relationship paths between tables. In this case, model calculations can use special functions to activate them.

17. Select OK, notice in the Manage Relationships window that the new relationship is listed, and then select Close.

18. Notice there’s now a connector between the two tables (it doesn’t matter if the tables are positioned next to each other).
- You can interpret the cardinality that is represented by the 1 and (*) indicators.
- Filter direction is represented by the arrow head.
- A solid line represents an active relationship; a dashed line represents an inactive relationship.
- Hover the cursor over the relationship to highlight the related columns.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image21.png)

There’s an easier way to create a relationship. In the model diagram, you can drag and drop columns to create a new relationship.

19. To create a new relationship using a different technique, from the Reseller table, drag the ResellerKey column onto the ResellerKey column of the Sales table.

Tip: Sometime a column doesn’t want to be dragged. If this situation arises, select a different column, and then select the column you intend to drag again, and then try again. Ensure that you see the new relationship added to the diagram.


20. Use the new technique to create the following two model relationships:

- Region | SalesTerritoryKey to Sales | SalesTerritoryKey
- Salesperson | EmployeeKey to Sales | EmployeeKey

21. In the diagram, arrange the tables so that the Sales table is positioned in the center of the diagram, and the related tables are arranged about it. Position the disconnected tables to the side.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image23.png)

22. In the report view, notice that the table visual updated to display different values for each product category.

- Filters applied to the Product table now propagate to the Sales table.

![](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image20.png)

23. Save the Power BI Desktop file.
# Configure Tables

In this exercise, you'll configure each table by creating hierarchies, and hiding, formatting, and categorizing columns.

## Configure the Product table

In this task, you'll configure the Product table.

1. In Model view, in the Data pane, if necessary, expand the Product table to reveal all fields.

2. To create a hierarchy, in the Data pane, right-click the Category column, and then select Create Hierarchy.

   ![Create hierarchy dialog.](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image24.png)

3. In the Properties pane (to the left of the Data pane), in the Name box, replace the text with "Products."

4. To add the second level to the hierarchy, in the Properties pane, in the Hierarchy dropdown list, select "Subcategory" (you might need to scroll down inside the pane).

5. To add the third level to the hierarchy, in the Hierarchy dropdown list, select "Product."

6. To complete the hierarchy design, select "Apply Level Changes."

   ![Hierarchy Design](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image26.png)

   Tip: Don’t forget to select "Apply Level Changes"—it’s a common mistake to overlook this step.

7. Notice the Products hierarchy in the Data pane.

   ![Products Hierarchy](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image27.png)

8. Expand the Products hierarchy to reveal the hierarchy levels.

   ![Expanded Hierarchy](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image28.png)

9. To organize columns into a display folder:
   - In the Data pane, first select the Background Color Format column.
   - While pressing the Ctrl key, select the Font Color Format column.
   - In the Properties pane, enter "Formatting" in the Display Folder box.

   ![Display Folder](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image29.png)

10. Notice that the two columns are now inside a folder. Display folders are a great way to declutter tables—especially for tables that comprise many fields. They’re for logical presentation only.

   ![Display Folder](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image30.png)

## Configure the Region table

In this task, you'll configure the Region table.

1. In the Region table, create a hierarchy named "Regions" with the following three levels:
   - Group
   - Country
   - Region

   ![Regions Hierarchy](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image31.png)

2. Select the Country column (not the Country hierarchy level).

3. In the Properties pane, expand the Advanced section (at the bottom of the pane), and then in the Data Category dropdown list, select "Country/Region."

   ![Data Category](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image32.png)

# Configure the Reseller table

In this task, you'll configure the Reseller table.

1. In the Reseller table, create a hierarchy named "Resellers" with the following two levels:
   - Business Type
   - Reseller.


2. Create a second hierarchy named "Geography" with the following four levels:
   - Country-Region
   - State-Province
   - City
   - Reseller.


3. Set the Data Category for the Country-Region, State-Province, and City columns (not the hierarchy level) to Country/Region, State or Province, and City, respectively.

## Configure the Sales table

In this task, you'll configure the Sales table.

1. In the Sales table, select the Cost column.

2. In the Properties pane, in the Description box, enter: "Based on standard cost."

   Descriptions can be applied to tables, columns, hierarchies, or measures. In the Data pane, description text is revealed in a tooltip when a report author hovers their cursor over the field.

3. Select the Quantity column.

4. In the Properties pane, from inside the Formatting section, slide the Thousands Separator property to Yes.

5. Select the Unit Price column.

6. In the Properties pane, from inside the Formatting section, set the Decimal Places property to 2.

7. In the Advanced group (you may need to scroll down to locate it), in the Summarize By dropdown list, select Average.

   By default, numeric columns will summarize by summing values together. This default behavior isn’t suitable for a column like Unit Price, which represents a rate. Setting the default summarization to average will produce a meaningful result.

## Bulk update properties

In this task, you'll update multiple columns using single bulk updates. You'll use this approach to hide columns and format column values.

1. In the Data pane, select the Product | ProductKey column.

2. While pressing the Ctrl key, select the following 13 columns (spanning multiple tables):

   - Region | SalesTerritoryKey
   - Reseller | ResellerKey
   - Sales | EmployeeKey
   - Sales | ProductKey
   - Sales | ResellerKey
   - Sales | SalesOrderNumber
   - Sales | SalesTerritoryKey
   - Salesperson | EmployeeID
   - Salesperson | EmployeeKey
   - Salesperson | UPN
   - SalespersonRegion | EmployeeKey
   - SalespersonRegion | SalesTerritoryKey
   - Targets | EmployeeID.


3. In the Properties pane, slide the Is Hidden property to Yes.

   The columns were hidden because they’re either used by relationships or will be used in row-level security configuration or calculation logic.

4. Multi-select the following three columns:

   - Product | Standard Cost
   - Sales | Cost
   - Sales | Sales.

5. In the Properties pane, from inside the Formatting section, set the Decimal Places property to 0 (zero).


# Review the Model Interface

In this exercise, you'll switch to Report view and review the model interface.

1. Review the model interface:
   - Switch to Report view.
   - In the Data pane, notice the following:
     - Columns, hierarchies, and their levels are fields, which can be used to configure report visuals.
     - Only fields relevant to report authoring are visible.
     - The SalespersonRegion table isn't visible because all of its fields are hidden.
     - Spatial fields in the Region and Reseller table are adorned with a spatial icon.
     - Fields adorned with the sigma symbol (Ʃ) will summarize by default.
     - A tooltip appears when hovering the cursor over the Sales | Cost field.
3. Expand the Sales | OrderDate field and notice that it reveals a date hierarchy.
   - The Targets | TargetMonth field delivers a similar hierarchy. These hierarchies weren't created by you. They were created automatically. However, there's an issue. The Adventure Works financial year commences on July 1 of each year, but in these automatically created date hierarchies, the date hierarchy year commences on January 1 of each year.

   ![Model Interface](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image40.png)

4. Turn off the automatic date behavior:
   - Navigate to File > Options and Settings > Options > Current File group, and select Data Load.
   - In the Time Intelligence section, uncheck Auto Date/Time.

   ![Turn Off Auto Date/Time](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image45.png)

6. In the Data pane, notice that the date hierarchies are no longer available.

## Create Quick Measures

In this exercise, you'll create two quick measures.

1. Create quick measures:
   - In the Data pane, right-click the Sales table and select New Quick Measure.

   ![Create Quick Measure](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image46.png   )

   - In the Quick Measures window, in the Calculation dropdown list, from inside the Mathematical Operations group, select Subtraction.

   ![Select Subtraction Operation](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image47.png)

   - In the Data pane of the Quick Measures window, expand the Sales table.
   - Drag the Sales field into the Base Value box.
   - Drag the Cost field into the Value to Subtract box.

   ![Create Subtraction Quick Measure](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image48.png   )

   - In the Data pane, inside the Sales table, a new measure will appear. Measures use the calculator icon.

   ![New Measure](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image50.png) 

   - To rename the measure, right-click it, select Rename, and then rename it to Profit.

2. Add a second quick measure:
   - Use the Division mathematical operation.
   - Set the Numerator to the Sales | Profit field.
   - Set the Denominator to the Sales | Sales field.
   - Rename the measure as Profit Margin.
   - Ensure the Profit Margin measure is selected, and on the Measure Tools contextual ribbon, set the format to Percentage with two decimal places.

   ![Create Division Quick Measure](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image54.png)

3. To test the two measures:
   - Select the table visual on the report page.
   - In the Data pane, check the two measures.

   ![Check Measures](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image55.png)

   - Select and drag the right guide to widen the table visual.

   ![Widen Table Visual](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image56.png)

   - Verify that the measures produce reasonable results that are correctly formatted.

   ![Verify Measures](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image57.png)

## Create a Many-to-Many Relationship

In this task, you’ll create a many-to-many relationship between the Salesperson table and the Sales table.

The labs use a shorthand notation to reference a field. It will look like this: `Salesperson | Salesperson`. In this example, "Salesperson" is the table name and "Salesperson" is the field name.

1. In Power BI Desktop, in Report view, in the Data pane, check the following two fields to create a table visual:

- Salesperson | Salesperson
- Sales | Sales

![Picture 1](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image9.png)

The table displays sales made by each salesperson. However, there’s another relationship between salespeople and sales. Some salespeople belong to one, two, or possibly more sales regions. In addition, sales reg ions can have multiple salespeople assigned to them.

From a performance management perspective, a salesperson’s sales (based on their assigned territories) need to be analyzed and compared with sales targets. You’ll create relationships to support this analysis in the next exercise.

2. Notice that Michael Blythe has sold almost $9 million.

3. Switch to Model view, then drag the SalespersonRegion table to position it between the Region and Salesperson tables.

4. Use the drag-and-drop technique to create the following two model relationships:

- Salesperson | EmployeeKey to SalespersonRegion | EmployeeKey
- Region | SalesTerritoryKey to SalespersonRegion | SalesTerritoryKey

The SalespersonRegion table can be considered a bridging table.

5. Switch to Report view, and then notice that the visual hasn’t updated—the sales result for Michael Blythe hasn’t changed.

6. Switch back to Model view, and then follow the relationship filter directions (arrowhead) from the Salesperson table.

Consider that the Salesperson table filters the Sales table. It also filters the SalespersonRegion table, but it doesn’t continue by propagating filters to the Region table (the arrowhead is pointing the wrong direction).

![Picture 380](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image11.png)

7. To edit the relationship between the Region and SalespersonRegion tables, double-click the relationship.

8. In the Edit Relationship window, in the Cross Filter Direction dropdown list, select Both.

9. Check the Apply Security Filter in Both Directions checkbox, then select OK.

![Picture 381](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image12.png)

10. Notice that the relationship has a double arrowhead now.

![Picture 382](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image14.png)

11. Switch to Report view, and then notice that the sales values    have still not changed.

The issue now relates to the fact that there are two possible filter propagation paths between the Salesperson and Sales tables. This ambiguity is internally resolved, based on a “least number of tables” assessment. To be clear, you shouldn’t design models with this type of ambiguity—the issue will be addressed in part later in this lab, and by the completion of the Create DAX Calculations in Power BI Desktop lab.

12. Switch to Model view to force filter propagation via the bridging table. Edit (double-click) the relationship between the Salesperson and Sales tables.

13. In the Edit Relationship window, uncheck the Make This Relationship Active checkbox, and select OK.

- The filter propagation will now follow the only active path.

14.In the diagram, notice that the inactive relationship is represented by a dashed line.

![Picture 5697](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image17.png)

Switch to Report view, and then notice that the sales for Michael Blythe are now nearly $22 million.

![Picture 5698](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image18.png)

Notice also, that the sales for each salesperson—if added—would exceed the table total.

It’s a common observation of a many-to-many relationship due to the double, triple, etc. counting of regional sales results. Consider Brian Welcker, the second salesperson listed. His sales amount equals the total sales amount. It’s the correct result due to the fact the he’s the Director of Sales; his sales are measured by the sales of all regions.

While the many-to-many relationship is now working, it’s now not possible to analyze sales made by a salesperson (because the relationship is inactive). You’ll be able to reactivate the relationship when you introduce a calculated table that will allow analyzing sales made in the sales region(s) assigned to the salesperson (for performance analysis) in the Create DAX Calculations in Power BI Desktop lab.

Switch to Modeling view, and then in the diagram, select the Salesperson table.

In the Properties pane, in the Name box, replace the text with Salesperson (Performance).

The renamed table now reflects its purpose: it’s used to report and analyze the performance of salespeople based on the sales of their assigned sales regions.

## Relate the Targets Table

In this task, you’ll create a relationship to the Targets table.

Create a relationship from the Salesperson (Performance) | EmployeeID column and the Targets | EmployeeID column.

In Report view, add the Targets | Target field to the table visual.

Resize the table visual so all columns are visible.

![Picture 5699](https://microsoftlearning.github.io/PL-300-Microsoft-Power-BI-Data-Analyst/Instructions/Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image19.png)

It’s now possible to visualize sales and targets—but take care for two reasons. First, there’s no filter on a time period, and so targets also include future target amounts. Second, targets aren’t additive, and so the total shouldn’t be displayed. They can either be disabled by formatting the visual or removed by using calculation logic. You’ll follow the second approach by creating a target measure in the Create Advanced DAX Calculations in Power BI Desktop lab that will return BLANK when more than one salesperson is filtered.

## Finish Up

In this task, you’ll complete the lab.

Save the Power BI Desktop file, and select Apply Later if prompted to apply queries.
