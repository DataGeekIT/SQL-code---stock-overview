# Queries-Repository - INVENTORY - SUPPLY CHAIN

This repository contains SQL queries for retrieving data from an ERP system, specifically related to transaction records. 
The queries extract information such as item details, warehouse transactions, order-related data, transaction types, and business partner information. 
The SQL queries also include conditional logic to determine whether a transaction represents an internal transfer.

**Table of Contents:**
It utilizes several SQL commands to extract specific information, as follows:

- `SELECT` statement: This command is used to query the database and select specific columns from the database tables. In this query, it selects various fields such as 'Item,' 'Warehouse,' 'Transaction Date,' 'Sequence,' 'Order Company,' 'Type of Order,' 'Order,' 'Order Line,' 'Order Sequence,' 'Transaction ID,' 'Quantity,' 'Transaction Type,' 'Site,' 'Receipt,' 'Shipment,' and 'Business Partner.'

- Subqueries: The query includes subqueries to fetch additional information. 

- Conditional Logic: The query employs a `CASE` statement to determine whether a transaction represents an internal transfer. 

- Table Joins: The SQL query performs table joins (LEFT JOIN) to link data from different tables in the ERP database, allowing for the retrieval of related information.

- Filtering: The `WHERE` clause is used to filter records based on specific conditions.
  
- Aggregation: The query uses the `TOP(1)` clause in subqueries to retrieve only the top (first) matching record, ensuring that a single result is returned for each subquery.


