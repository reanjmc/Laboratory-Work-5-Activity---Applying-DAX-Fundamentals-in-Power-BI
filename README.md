# Laboratory-Work-5-Activity---Applying-DAX-Fundamentals-in-Power-BI


### 1. Measures vs. Calculated Columns

Measures and calculated columns are both used in DAX, but they serve different purposes. A calculated column is computed row by row and stored in the dataset. It is useful when values need to be categorized or filtered permanently, such as creating a “Profit” column or labeling customers as “VIP.” Measures, on the other hand, are calculated dynamically based on the current filter context. For example, a Total Sales measure changes automatically depending on selected dates, regions, or products.

A calculated column increases memory usage because results are stored in the model, while measures are more memory efficient since calculations happen only when needed. Measures are also more flexible for dashboards and interactive reports because they respond to slicers and filters dynamically. Therefore, calculated columns are best for static row-level calculations, while measures are ideal for aggregations and dynamic analysis.
