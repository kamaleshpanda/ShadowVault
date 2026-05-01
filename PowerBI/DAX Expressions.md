**DAX (Data Analysis Expressions)** in Power BI are formulas used to create calculations on your data.
*Normally we use basic aggregations like SUM and MAX, but DAX allows advanced and context-based calculations.*

### Simple examples:
- `Total Sales = SUM(Sales[Amount])`
- `Profit = SUM(Sales[Revenue]) - SUM(Sales[Cost])`
- `Year = YEAR(Sales[Date])`

```
MeasureName =  FUNCTION(Table[Column]) ........
```