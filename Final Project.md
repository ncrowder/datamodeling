---


---

<h1 id="final-project-data-modeling">Final Project (Data Modeling)</h1>
<p><em>Purpose: To showcase your understanding of basic dimensional modeling techniques and associated sql queries.</em></p>
<h2 id="part-1">Part 1:</h2>
<p>Create a star schema database (‘st_username_dmfinal’) in sql server from one of the following options (I will assign each student to one of these):</p>
<ul>
<li>FactShipment (grain: per shipment)
<ul>
<li>measures: Weight, Distance, and FreightCost</li>
<li>dimensions: Shipper, Date, DestinationState</li>
</ul>
</li>
<li>FactProduction (grain: per batch)
<ul>
<li>measures: UnitsProduced, ScrapQty, MachineHours</li>
<li>dimensions: Date, Product, Employee</li>
</ul>
</li>
</ul>
<p>Additional Requirements:</p>
<ul>
<li>Fact table with synthetic PK starting at 1000 and incrementing by 1 for each new row.</li>
<li>Fact tables is joined to each requested dim table through a valid foreign key relationship (i.e. foreign key constraint).</li>
<li>For the date dimension use the same one that we created for class (fact_sales_500). <strong>Use ‘SELECT * FROM [source] INTO [destination]’ for this.</strong></li>
<li>For the other two dimensions you should have at least 3 attributes besides the primary key.</li>
<li>Appropriate and defendable choices for data type and nullability for all columns in all tables.  There needs to be at least one unique column (besides the primary keys) and at least one column that uses a default value.</li>
<li>At least 100 rows of data in your fact table and 10 rows in each of your non date dimensions.  (Make sure your dates in your fact table are from 2025 since that’s what our DimDate uses.)  <em>Note: You will likely need to use a tool like <a href="www.tableconvert.com">Table Convert</a> where you can upload a csv (if you are using a site like Mockaroo to generate your data) and it will create the sql statement needed to quickly populate your table.  If you had access to the server itself you could upload the csv to the server and use a bulk insert and just reference the file.  If you used your own instance of SQL Server running locally on your machine you could do this as well, but then no one would be able to access it but you, since it wouldn’t be on the network.</em></li>
</ul>
<h2 id="part-2">Part 2:</h2>
<p>One SQL Query from each of the dimensions to the fact that involves an aggregation (three total).<br>
Two SQL Queries that uses two dimensions and an aggregation along with a groupby/having.</p>
<p>For each of these queries show the query, the result, and explain in simple English what it’s finding, and why it might be a useful thing to look at (i.e. what might one use the results to do or what action might be taken?)</p>
<h2 id="part-3">Part 3:</h2>
<p>Create the FactInventory_Monthly, FactOrders, and both the DimCustomer_SCD2 and DimCustomer_SCD3 tables from the provided scripts.</p>
<p>Additional Requirements:</p>
<ul>
<li>Add in 2 more products to the Factinventory_Monthy table.
<ul>
<li>Make sure the FactInventory_Monthly table records all the product inventories for the first 6 months of 2024.</li>
<li>Create a view called v_FactInventory_MonthlyAvg that shows all the data in the table but also a column for AverageInventory and AverageValue by ProductID.  Querying the view should still return 24 rows of data.</li>
</ul>
</li>
<li>Add in 2 more orders to the FactOrders table both from 2025.
<ul>
<li>One order should go all the way through to delivery and take more than 10 days.</li>
<li>One order should go through to ship, but not delivery, and it should take more than 7 days to ship.</li>
<li>Create a view V_FactOrders_Problems that returns all rows from FactOrders where either DaystoShip is greater than 7 or DaystoDeliver is more than 10.  Clearly, querying the view should return 2 rows.</li>
</ul>
</li>
<li>Add in two more customers to the DimCustomer_SCD2 and DimCustomer_SCD3 tables.
<ul>
<li>Perform the same update to the same customer in both the SCD2 and SCD3 tables.</li>
</ul>
</li>
</ul>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

