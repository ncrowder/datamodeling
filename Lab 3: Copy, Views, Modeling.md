---


---

<h1 id="lab-3-copying-tables-adding-rows-creating-views--conceptuallogical-modeling"><strong>Lab 3: Copying Tables, Adding Rows, Creating Views &amp; Conceptual/Logical Modeling</strong></h1>
<p>By now we’ve worked with basic and intermediate sql queries and done some ER diagramming.  The goal of this next lab is to have you create your own databases and work further to refine your data modeling skills.</p>
<h2 id="part-1">Part 1:</h2>
<ol>
<li>
<p>Create your own database on the server titled ‘st_[username]_basicsqllab’. <em>(Right click on Databases folder in Object Explorer and choose “New Database…”)</em>  You can use the defaults for everything.</p>
</li>
<li>
<p>Then execute the following code to copy over the rows from the Customers table into your own database.</p>
</li>
</ol>
<pre><code>SELECT *
INTO dbo.Customers
FROM basicsqllab.dbo.Customers
</code></pre>
<p><strong>Make sure you are in your own database when you execute the query.  Now do this for all 4 tables in the basicsqllab database.</strong></p>
<ol start="3">
<li>Insert a new order into the Orders table as such:</li>
</ol>
<pre><code>INSERT INTO Orders
VALUES 
(70, 41, '2024-11-02', 'Delivered', 'NC')
(71, 51, '2024-08-03', 'Shipped', 'HI')
</code></pre>
<ol start="3">
<li>While whether the column allows nulls (its nullability) and its datatype should copy over, the primary key and foreign key constraints have to be set manually.  Execute the following statements one a time to set up the keys between Customers and Orders in an attempt to set the keys.  <strong>Does everything work as you?  Explain any errors you receive and why you believe they are happening.</strong></li>
</ol>
<pre><code>ALTER TABLE dbo.Customers
ADD CONSTRAINT PK_Customers
PRIMARY KEY (CustomerID);
</code></pre>
<pre><code>ALTER TABLE dbo.Orders
ADD CONSTRAINT FK_Orders_Customers
FOREIGN KEY (CustomerID)
REFERENCES dbo.Customers(CustomerID);
</code></pre>
<ol start="4">
<li>
<p>Make any other additions or changes to the database tables necessary to resolve any errors from step 3, but do not remove either or the orders you inserted in step 2.  <strong>Explain what you did.</strong></p>
</li>
<li>
<p>Repeat the process for setting all the primary key and foreign key constraints for the remainder of the tables.</p>
</li>
<li>
<p>Insert at least two more rows of your own data into each table.</p>
</li>
</ol>
<h2 id="part-2">Part 2:</h2>
<p>You will now create a couple different views in your new database.  Views are essentially just queries that are stored on the server that you can can run without rewriting queries from scratch each time or loading *.sql files.  They provide quick retrieval of commonly used data and metrics and can be created by those who know SQL (analysts) so they can be run by those who don’t (end users).</p>
<ol start="7">
<li>Create your first view by executing this:</li>
</ol>
<pre><code>CREATE VIEW vCustomerOrders
AS
SELECT
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email,
    COUNT(o.OrderID) AS OrderCount
FROM Customers as c
LEFT JOIN Orders as o
    ON c.CustomerID = o.CustomerID
GROUP BY
    c.CustomerID,
    c.FirstName,
    c.LastName,
    c.Email;
</code></pre>
<p>After executing this the view has now been saved on your database and you should be able to open the views folder in Object Explorer and confirm that is the case.  You can see the “view” by running the following:</p>
<pre><code>SELECT * from vCustomerOrders
</code></pre>
<ol start="8">
<li>Explain the repercussions of choosing a LEFT JOIN to create the view.  What would be the reasons for doing this?  What would change if you were to use a RIGHT JOIN (or switch the table order and use a LEFT JOIN)?</li>
</ol>
<p>You can treat the view like any other table in the database and so you are able to change the SELECT and add conditions using WHERE, or group the results using GROUPBY and limit the groups that get returned using HAVING.</p>
<ol start="9">
<li>
<p>Write a new query using the view you created to return only those rows with customers having multiple orders.  <strong>Give the query and a screenshot of the results.</strong></p>
</li>
<li>
<p>Write a new query using the view you created to return only those rows with customers having multiple orders.  <strong>Give the query and a screenshot of the results.</strong>  Hint:</p>
</li>
</ol>
<pre><code>SELECT * from vCustomerOrders
WHERE Email LIKE ________ OR Email LIKE _________ 
</code></pre>
<ol start="11">
<li>Create your own view.  It doesn’t need to use the Customers table.  It should however involve at least one join and some kind of aggregation (count, sum, average, min, max).  Name your view starting with v* and make it descriptive.</li>
</ol>
<h2 id="part-3">Part 3:</h2>
<p>In this section we’ll begin a modeling exercise.  You will turn in two diagrams.  <strong>You can use paper and take a high-res scan (I recommend AdobeScan or CamScanner). OR use <a href="http://draw.io">draw.io</a> or lucidchart.</strong> You will do a conceptual model in the first, and a logical model in the second.  You can choose any domain you like (Human Resources, Library, Hotel, Banking, Airline, you name it…).  Just make sure you can identify at least 5 entities, but ideally between 6-8.</p>
<ol start="12">
<li>For the conceptual, recall that a conceptual model should be limited to between 5-10 entities (in our case) and should only include the following conventions:</li>
</ol>
<ul>
<li>Dotted or Solid Lines to show whether the relationship is identifying or non-identifying.  Recall that relationships may also be recursive (two instances of same entity related).</li>
<li>Symbols denoting optionality (whether relationship is required) and cardinality (1:1, 1:M, M:N)</li>
<li>No bridging/junction tables (M:N are allowable)</li>
<li>Pointed or rounded entities to denote if they are strong or weak.</li>
<li>Subtypes (if applicable)</li>
</ul>
<ol start="13">
<li>Build the the logical model from the conceptual model and add the following:</li>
</ol>
<ul>
<li>Attributes</li>
<li>Identification of PK and FK (if applicable) for all tables</li>
<li>Normalization</li>
<li>Elimination of M:N relationships with bridging tables</li>
<li>Possible refinement (addition or elimination) of any subtypes previously decided upon in the conceptual stage.</li>
</ul>
<ol start="14">
<li>Finally, and this pushes a bit into the physical stage implementation, decide whether any any of the attributes should accept null values or be unique (other than the chosen primary key).  For any columns that have allow null values, should there be a default value inserted instead of a null?</li>
</ol>
<p><strong>Comment on any of these concerns that might be applicable and which entities (relations) and which attributes they might apply to.</strong></p>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

