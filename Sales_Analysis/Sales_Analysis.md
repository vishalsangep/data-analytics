Company: AtliQ hardware
	  Computer Hardware & Peripheral Manufacturer

Problem Statement : Issues in tracking sales over the different branches across India

Poject planned over AIMS Grid


Purpose:
To unlock sales insights that are not visible before for sales team for decision 
support & automate them to reduce manual time spent in data gathering.

Stake Holders:
* Sales Director
* Marketing Team
* Customer Service Team
* Data & Analytics Team
* IT

End Result:
An automated dashboard providing quick & latest sales insights in order to support
data driven decision making.

Success Criteria:
* Dashboard(s) uncovering sales order insights with latest data available
* Sales team able to take better decisions & prove 10% cost savings of total spend
* Sales analysts stop data gathering manually in order to save 20% of their business time and reinvest it in value added activity




data gathering:

IT team has a sales management system which is a simple software that keeps track of all the sales number. So whenever aproduct is sold in any local region this software prints the invoice so it has all the records stored in a MySQL database. 



data cleaning: 
* found sales_amount values less than or equal to zero in sale transaction table and removed/filtered them out in power query

* found few transactions/records in sales_amount in USD, so created a new column "norm_sales_amount" to convert all USD in the sales_amount to INR.
		
	DAX formula: = Table.AddColumn(#"Filtered Rows", "norm_sales_amount", each if [currency] = "USD#(cr)" then [sales_amount]*83 else [sales_amount])

* market is India ,found two international markets in the sales market table and filtered them out.
 
* found blank data report to data engineering team


SQL used for cross checking dashboard

SELECT *,
  CASE
    WHEN transactions.currency = 'USD/r' THEN sales_amount * 83
    ELSE sales_amount
  END AS norm_sales_amount
FROM transactions where sales_amount > 0 ;


CREATE TEMPORARY TABLE temp_table AS
SELECT *,
  CASE
    WHEN transactions.currency = 'USD/r' THEN sales_amount * 83
    ELSE sales_amount
  END AS norm_sales_amount
FROM transactions
WHERE sales_amount > 0;


SELECT * FROM temp_table;

SELECT SUM(temp_table.sales_amount) FROM temp_table INNER JOIN date ON temp_table.order_date=date.date where date.year=2020
and temp_table.market_code="Mark001";


#SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark00

Note:
In dashboard 1.2 additional columns are added to sales transaction table for further analysis

DAX measures used:

Profit Margin % = DIVIDE([Total profit margin],[Revenue],0)

Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))

Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))


