# ERP-Data-Queries-Repository - ON STOCK INVENTORY - SUPPLY CHAIN

This repository contains SQL queries for retrieving data from an ERP system, specifically related to transaction records. 
The queries extract information such as item details, warehouse transactions, order-related data, transaction types, and business partner information. 
The SQL queries also include conditional logic to determine whether a transaction represents an internal transfer.

**Table of Contents:**
It utilizes several SQL commands to extract specific information, as follows:

- `SELECT` statement: This command is used to query the database and select specific columns from the database tables. In this query, it selects various fields such as 'Item,' 'Warehouse,' 'Transaction Date,' 'Sequence,' 'Order Company,' 'Type of Order,' 'Order,' 'Order Line,' 'Order Sequence,' 'Transaction ID,' 'Quantity,' 'Transaction Type,' 'Site,' 'Receipt,' 'Shipment,' and 'Business Partner.'

- Subqueries: The query includes subqueries to fetch additional information. For example, it retrieves the 'Type of Order Desc' and 'Transaction Type Desc' by joining the `t1` and `t2` tables from the ERP database. These subqueries provide descriptions for the 'Type of Order' and 'Transaction Type' values.

- Conditional Logic: The query employs a `CASE` statement to determine whether a transaction represents an internal transfer. It checks if the 't_koor' value matches specific criteria for internal transfers and assigns 'Yes' or 'No' accordingly.

- Table Joins: The SQL query performs table joins (LEFT JOIN) to link data from different tables in the ERP database, allowing for the retrieval of related information.

- Filtering: The `WHERE` clause is used to filter records based on specific conditions. For example, it filters records where 't_cpac' is 'tc,' 't_cdom' is 'koor,' and 't_clan' is '2' for the 'Type of Order Desc' subquery.

- Aggregation: The query uses the `TOP(1)` clause in subqueries to retrieve only the top (first) matching record, ensuring that a single result is returned for each subquery.



Please note that this code is designed to work with specific ERP database tables and may require customization for different ERP systems. 
Use these SQL queries as a reference or starting point for querying ERP data.
