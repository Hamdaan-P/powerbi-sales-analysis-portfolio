## Sales
`Sales = SUM(Orders_Clean[Sales])`  
Simple aggregation of sales.

## Profit
`Profit = SUM(Orders_Clean[Profit])`  
Sum of profit per context.

## Orders Count
`Orders Count = DISTINCTCOUNT(Orders_Clean[Order ID])`  
Count of unique order IDs.

## Profit Margin %
`Profit Margin % = DIVIDE([Profit], [Sales], 0)`  
Profit divided by Sales.

## Sales YTD
`Sales YTD = TOTALYTD([Sales], 'Date'[Date])`  
Year-to-date sales using the Date table.

## Sales PY  
Sales PY = CALCULATE ( [Sales], SAMEPERIODLASTYEAR ( 'Date'[Date] ) )
Calculates prior year sales using SAMEPERIODLASTYEAR for time-based comparison.

## Sales YoY %  
Sales YoY % = DIVIDE ( [Sales]- [Sales PY],[Sales PY],0 )
Computes year-over-year sales growth as a percentage change from last year.

## Avg Order Value  
Avg Order Value = DIVIDE ( [Sales], [Orders Count], 0)
Returns the average revenue per order by dividing total sales by total orders.

## Pareto Threshold  
Pareto Threshold = 0.8
Defines the 80% cutoff used in Pareto analysis to identify top-performing customers.

## Customer Avg Order Value  
Customer Avg Order Value = DIVIDE([Customer Sales], [Customer Orders Count], 0)
Calculates the average order value per customer based on their total sales and order count.

## Customer Cumulative Sales 
Customer Cumulative Sales = 
VAR CurrRank = [Customer Sales Rank]
RETURN
CALCULATE(
  [Sales],
  FILTER(
    ALLSELECTED( Orders_Clean[Customer Name] ),
    RANKX( ALLSELECTED( Orders_Clean[Customer Name] ), [Sales], , DESC, DENSE ) <= CurrRank
  )
)
Aggregates sales for top-ranked customers up to the current customer's rank using RANKX.

## Customer Cumulative Sales %  
Customer Cumulative Sales % = 
DIVIDE(
  [Customer Cumulative Sales],
  CALCULATE( [Sales], ALLSELECTED( Orders_Clean[Customer Name] ) ),
  0
)
Shows the cumulative sales contribution of a customer relative to total selected sales.


## Customer First Order 
Customer First Order = MIN(Orders_Clean[Order Date]) 
Returns the date of the customer's earliest recorded order.


## Customer Last Order
Customer Last Order = MAX(Orders_Clean[Order Date])  
Returns the date of the customer's most recent recorded order.

## Customer Orders Count  
Customer Orders Count = [Orders Count]
Represents the total number of orders placed by the customer.

## Customer Profit  
Customer Profit = [Profit]
Returns the total profit attributed to the customer.

## Customer Return Rate %  
Customer Return Rate % = 
DIVIDE([Customer Returned Orders], [Customer Orders Count], 0)
Calculates the percentage of a customer's orders that were returned.

## Customer Returned Orders  
Customer Returned Orders = 
CALCULATE(
  DISTINCTCOUNT(Orders_Clean[Order ID]),
  Orders_Clean[IsReturned] = 1
)
Counts the distinct number of returned orders for a customer.

## Customer Sales  
Customer Sales = [Sales]
Returns the total sales attributed to the customer.

## Customer Sales Rank  
Customer Sales Rank = 
RANKX(
  ALLSELECTED( Orders_Clean[Customer Name] ),
  [Sales],
  ,
  DESC,
  DENSE
)
Ranks customers by their sales volume in descending order using RANKX.

## Drill Customer  
Drill Customer = 
IF(HASONEVALUE(Orders_Clean[Customer Name]), VALUES(Orders_Clean[Customer Name]), "Multiple / All")
Displays the selected customer name or "Multiple / All" when multiple customers are selected.
















