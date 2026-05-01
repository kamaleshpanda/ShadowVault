**DAX (Data Analysis Expressions)** in Power BI are formulas used to create calculations on your data.
*Normally we use basic aggregations like SUM and MAX, but DAX allows advanced and context-based calculations.*

### Simple examples:
- `Total Sales = SUM(Sales[Amount])`
- `Profit = SUM(Sales[Revenue]) - SUM(Sales[Cost])`
- `Year = YEAR(Sales[Date])`

``` DAX
MeasureName =  FUNCTION(Table[Column]) ........
```

Example:-
``` DAX
Total_Sales = SUMX( customer_purchases,customer_purchases[quantity] *                                customer_purchases[cost_to_customer_per_qty])
```
###### **SUMX (Iterator Function)**
- **SUMX** is an **iterator function**.
- It goes **row by row** over a table and performs a calculation.
### **Expression inside SUMX**

```
customer_purchases[quantity] * customer_purchases[cost_to_customer_per_qty]
```

- For **each row**, it calculates:
    - Quantity × Cost per quantity
- This gives **sales value per row**

---
## **How it works (step-by-step logic)**

|quantity|cost_per_qty|Row Calculation|
|---|---|---|
|2|100|2 × 100 = 200|
|3|150|3 × 150 = 450|
|1|200|1 × 200 = 200|

 Then SUMX adds all:
```
Total_Sales = 200 + 450 + 200 = 850
```

---
### **Important Concepts (Very Important)**  #imp 
- **Row Context** → SUMX creates a row-by-row evaluation
- **Iterator Function** → SUMX processes each row individually
- **Dynamic Result** → Changes based on filters (like slicers)

