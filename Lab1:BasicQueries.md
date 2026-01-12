---


---

<h1>Lab 1 - Fundamental T-SQL Queries</h1>
<p><em>Directions: Complete the following queries and save your file as “lab1-lastname.sql”  and make sure each query is commented with the number and directions, for example:</em></p>
<pre><code>-- 1. Return all columns from 'dbo.Customers' 
</code></pre>
<h2 id="a.-select-basics">A. SELECT Basics</h2>
<ol>
<li>
<p>Return all columns from <code>dbo.Customers</code>.</p>
</li>
<li>
<p>Return <code>CustomerID</code>, <code>FirstName</code>, <code>LastName</code>, and <code>StateCode</code> for customers in <strong>WI</strong>.</p>
</li>
<li>
<p>Return inactive products (<code>IsActive = 0</code>) showing <code>ProductID</code>, <code>ProductName</code>, and <code>UnitPrice</code>.</p>
</li>
<li>
<p>Return all orders with <code>Status = 'Shipped'</code>, sorted by <code>OrderDate</code> from newest to oldest.</p>
</li>
<li>
<p>Return customers who signed up in <strong>2025</strong>.</p>
</li>
<li>
<p>Return orders where <code>ShipState</code> is <strong>WI or IL</strong>.</p>
</li>
<li>
<p>Return products priced between <strong>$10 and $30</strong> (inclusive), sorted by <code>UnitPrice</code>.</p>
</li>
<li>
<p>Return customers whose <code>Email</code> is <strong>NULL</strong>.</p>
</li>
<li>
<p>Return customers whose <code>LastName</code> starts with the letter <strong>G</strong>.</p>
</li>
</ol>
<hr>
<h2 id="b.-computed-columns--functions">B. Computed Columns &amp; Functions</h2>
<ol start="10">
<li>
<p>From <code>dbo.OrderItems</code>, return <code>OrderID</code>, <code>ProductID</code>, <code>Quantity</code>, <code>UnitPrice</code>, and a computed column <code>LineSubtotal = Quantity * UnitPrice</code>.</p>
</li>
<li>
<p>From <code>dbo.OrderItems</code>, compute a column <code>LineTotal = Quantity * UnitPrice * (1 - DiscountPct)</code> and round it to <strong>2 decimal places</strong>.</p>
</li>
<li>
<p>From <code>dbo.Customers</code>, return <code>CustomerID</code>, a computed column <code>FullName</code> (<code>FirstName + ' ' + LastName</code>), <code>City</code>, and <code>StateCode</code>, sorted alphabetically by <code>FullName</code>.</p>
</li>
<li>
<p>From <code>dbo.Customers</code>, return <code>CustomerID</code>, <code>Email</code>, and a computed column <code>HasEmail</code> that is <code>1</code> if <code>Email</code> is NOT NULL and <code>0</code> if <code>Email</code> IS NULL.</p>
</li>
<li>
<p>From <code>dbo.Products</code>, return <code>ProductName</code>, <code>UnitPrice</code>, and a computed column <code>PriceTier</code>:</p>
<ul>
<li><code>Low</code> if price &lt; 15</li>
<li><code>Medium</code> if price between 15 and 40</li>
<li><code>High</code> if price &gt; 40</li>
</ul>
</li>
<li>
<p>From <code>dbo.Orders</code>, return <code>OrderID</code>, <code>OrderDate</code>, and a computed column <code>OrderMonth</code> showing the month name, sorted by <code>OrderDate</code>.</p>
</li>
<li>
<p>From <code>dbo.Customers</code>, return <code>CustomerID</code>, <code>LastName</code>, and a computed column <code>LastNameInitial</code> (first letter of last name), sorted by <code>LastNameInitial</code> then <code>LastName</code>.</p>
</li>
</ol>
<hr>
<h2 id="c.-aggregates--group-by">C. Aggregates &amp; GROUP BY</h2>
<ol start="17">
<li>
<p>Count how many orders exist for each <code>Status</code>. Return <code>Status</code> and <code>OrderCount</code>.</p>
</li>
<li>
<p>Find the average product price for each <code>Category</code>, rounded to <strong>2 decimals</strong>, sorted from highest to lowest average.</p>
</li>
<li>
<p>From <code>dbo.Orders</code>, return <code>ShipState</code> and the total number of orders shipped to each state, sorted from highest to lowest count.</p>
</li>
<li>
<p>From <code>dbo.OrderItems</code>, return <code>ProductID</code> and the <strong>average quantity per line item</strong> for each product.</p>
</li>
<li>
<p>From <code>dbo.Customers</code>, return <code>StateCode</code> and the number of customers in each state, including only the state code and the count.</p>
</li>
</ol>
<hr>
<h2 id="d.-group-by-with-having">D. GROUP BY with HAVING</h2>
<ol start="22">
<li>
<p>From <code>dbo.OrderItems</code>, return <code>OrderID</code> and the number of line items per order, including only orders with <strong>2 or more</strong> line items.</p>
</li>
<li>
<p>From <code>dbo.OrderItems</code>, return <code>ProductID</code> and the total quantity ordered, including only products with total quantity <strong>greater than or equal to 3</strong>.</p>
</li>
<li>
<p>From <code>dbo.Orders</code>, return <code>CustomerID</code> and the total number of orders per customer, including only customers with <strong>3 or more</strong> orders.</p>
</li>
<li>
<p>From <code>dbo.OrderItems</code>, return <code>OrderID</code> and the <strong>total extended order value</strong><br>
(<code>SUM(Quantity * UnitPrice)</code>), including only orders with a total value <strong>greater than $100</strong>.</p>
</li>
<li>
<p>From <code>dbo.Products</code>, return <code>Category</code> and the number of products in each category, including only categories with <strong>at least 5 products</strong>.</p>
</li>
</ol>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

