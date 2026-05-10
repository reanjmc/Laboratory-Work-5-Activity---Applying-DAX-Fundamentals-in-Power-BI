# Laboratory-Work-5-Activity---Applying-DAX-Fundamentals-in-Power-BI


### 1. Measures vs. Calculated Columns

Measures and calculated columns are both used in DAX, but they serve different purposes. A calculated column is computed row by row and stored in the dataset. It is useful when values need to be categorized or filtered permanently, such as creating a “Profit” column or labeling customers as “VIP.” Measures, on the other hand, are calculated dynamically based on the current filter context. For example, a Total Sales measure changes automatically depending on selected dates, regions, or products.

A calculated column increases memory usage because results are stored in the model, while measures are more memory efficient since calculations happen only when needed. Measures are also more flexible for dashboards and interactive reports because they respond to slicers and filters dynamically. Therefore, calculated columns are best for static row-level calculations, while measures are ideal for aggregations and dynamic analysis.


### 2. Time Intelligence in Business Decisions

DAX time intelligence functions such as TOTALYTD and SAMEPERIODLASTYEAR help organizations analyze trends over time. TOTALYTD calculates cumulative sales from the start of the year up to the current date, while SAMEPERIODLASTYEAR compares current performance with the same period in the previous year.

These functions support business decisions by allowing managers to track growth, identify seasonal trends, and evaluate company performance accurately. Unlike simple Excel formulas, DAX time intelligence automatically works with calendars, filters, and relationships across tables. This makes analysis faster, more accurate, and scalable for large datasets. DAX also updates dynamically when users interact with reports, making it more powerful for business intelligence.


### 3. Filter Context and CALCULATE

The CALCULATE function is one of the most important functions in DAX because it modifies filter context. Filter context refers to the conditions applied to data during calculations. For example:

USA Revenue=CALCULATE(SUM(Sales[Revenue]), Sales[Country]="USA")

This formula changes the filter context so only USA sales are included in the calculation.

CALCULATE is important for dynamic reporting because users can interact with filters and slicers while measures update automatically. In Excel, filtering is mostly static and often requires manual formulas or pivot table adjustments. In Power BI, CALCULATE provides more advanced and flexible analysis, making reports interactive and responsive.


### 4. Iterator Functions (SUMX, AVERAGEX)

Iterator functions such as SUMX and AVERAGEX perform calculations row by row before aggregating results. They are useful when calculations involve expressions instead of direct column totals.

For example, if shipping cost depends on quantity multiplied by shipping rate for each order, SUMX can calculate each row first and then sum the results.

SUMX(Orders, Orders[Quantity]×Orders[ShippingRate])

Using SUM alone would only total a single column and could not evaluate row-level expressions. Iterator functions provide more accurate calculations for complex business scenarios, especially in finance, logistics, and sales analysis.


### 5. Optimization with Variables

Variables in DAX are created using VAR and RETURN. They improve readability, performance, and debugging by storing intermediate results in a formula.

Example:Discounted Sales =
VAR TotalSales = SUM(Sales[Amount])
VAR Discount = TotalSales * 0.10
RETURN
TotalSales - Discount
Variables improve performance because calculations are performed once and reused instead of repeated multiple times. They also make formulas easier to understand and debug since developers can test each variable separately. This is especially useful in complex calculations where repeated expressions slow report performance.



### 6. Distinct Values with VALUES

The VALUES function returns a list of distinct values from a column. For example, VALUES(City[Name]) returns all unique cities in the dataset.

Retrieving distinct values is important because businesses often need to count unique customers, cities, products, or transactions. Combining VALUES with other functions provides deeper insights.
For example: 
Unique Cities = COUNTROWS(VALUES(Sales[City]))
This formula counts how many different cities contribute to sales. Distinct value analysis helps organizations identify market reach, customer diversity, and regional performance.


### 7. Calculated Columns for Categorization

A calculated column is appropriate for categorizing orders because the classification is performed row by row and stored permanently in the dataset.

Example: This makes it easy to filter, group, and visualize high-value orders in reports. Measures are less suitable because they calculate dynamically and do not store row-level categories.

The trade-off is that calculated columns consume more storage memory since results are saved in the data model. Measures are more flexible and memory efficient, but calculated columns are better for fixed categorizations used repeatedly across reports.


### 8. Logical Functions in Decision Rules

Logical functions such as IF, AND, OR, and NOT are used in DAX to create business rules and automate decision-making.

Example:Performance Level =
IF(
    AND(Employee[Score] >= 85, Employee[Attendance] >= 90),
    "Excellent",
    "Needs Improvement"
)
These functions allow organizations to classify employees, customers, or products based on specific conditions. Logical structuring is critical in BI models because it ensures consistent decision rules, improves automation, and reduces human error. Well-designed logic also helps businesses create reliable dashboards and accurate reports for management decisions.


### 9. Advantages of DAX in Power BI

DAX in Power BI offers many advantages compared to traditional Excel formulas. One major advantage is scalability. Power BI can handle millions of rows of data efficiently, while Excel becomes slow with very large datasets.

Another advantage is context awareness. DAX calculations automatically respond to filters, slicers, and relationships between tables. This allows users to perform advanced analytics dynamically without manually changing formulas. Excel formulas are more static and usually require manual adjustments.

DAX is also integrated into the broader BI ecosystem of Power BI, enabling connections to databases, cloud services, and real-time dashboards. Businesses can combine data from multiple sources and create interactive visualizations for faster decision-making. Overall, DAX provides greater flexibility, automation, and analytical power for modern business intelligence compared to traditional Excel spreadsheets.


### 10. DAX Studio for Performance Tuning

DAX Studio is a tool used to analyze and optimize DAX queries in Power BI. It helps developers identify slow calculations, measure query execution time, and understand how the engine processes requests.

Using DAX Studio, developers can check server timings, query plans, and storage engine performance. This helps locate inefficient formulas or unnecessary calculations that slow reports down.

Query optimization is important for large datasets because poorly written queries can increase loading times and reduce report responsiveness. Faster queries improve user experience by making dashboards more interactive and reducing waiting time for report updates. Optimized reports also reduce system resource usage and improve overall business productivity.


