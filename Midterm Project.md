---


---

<h1 id="midterm-project-data-modeling">Midterm Project (Data Modeling)</h1>
<h2 id="part-1-reflection---20-points">Part 1 (Reflection) - 20 points</h2>
<p>Look back at all comments left on any of the labs or discussion posts and make sure you understand them, to include Lab 3 and Discussion 3 comments as well (which I’ll complete by EOD Friday).  Submit in a word document your responses or reflections to any comments which indicated you missed a step or had a misunderstanding about something.  Put your comments under a heading tied to the lab or discussion within your document.  Be prepared to answer follow-up questions about them during the final exam / interview.</p>
<h2 id="part-2-erd---40-points">Part 2 (ERD) - 40 points</h2>
<ol>
<li>Create and submit a <em>conceptual</em> ERD with the following requirements:</li>
</ol>
<ul>
<li>Five or more entities (at least one weak entity) where strong entities are pointed and weak are rounded.</li>
<li>Make sure all relationships are shown as either optional or mandatory and include the cardinality on both sides.</li>
<li>Show the strength or relationships (either identifying or non-identifying) between any parent child relationships that exist that are 1:M with either a solid or dashed line.</li>
<li>Treat any relationship between strong entities as non-identifying unless the relationship is M:N in which case show this with a solid line (this is the convention our textbook uses).</li>
<li>Weak entities should have one or more identifying relationships to support it.</li>
<li>Include subtypes as part of one of the entities (but don’t treat these as one of the required 5 entities).</li>
<li>Recursive relationships are optional.</li>
</ul>
<p><strong>Make sure you also give a paragraph explaining in general terms what the data model represents (what subject area) and what it will be used for.</strong></p>
<ol start="2">
<li>From the conceptual ERD create a logical ERD with the following requirements:</li>
</ol>
<ul>
<li>Add bridging tables where there were M:N relationships in the conceptual design.</li>
<li>Identify the unique identifier for each relation (entity).</li>
<li>Add at least 5 attributes to each entity besides the unique identifiers (pk) and associated parent identifiers (fk).  For each attribute, list whether it’s a string, numeric, date, currency (i.e. money), or Boolean (T/F).</li>
<li>Ensure that the design is normalized to 3NF.</li>
</ul>
<p><em>Note: Even though in reality the keys tell the full story about whether an entity is weak and how it’s being identified, the book continues to use solid/rounded rectangles and solid/dashed lines even within the logical models.</em></p>
<ol start="3">
<li>Answer the following:</li>
</ol>
<ul>
<li>Would any of the attributes other than the primary key be unique?  Such as if you chose a synthetic (or surrogate) key, but there is also a natural (business) key.</li>
<li>Are any of the columns nullable (should allow null values)?  If so, why?  And do you think there should be a default value supplied if a user tries inserting a row without specifying a value?  Explain.</li>
</ul>
<h2 id="part-3-ssms--sql---40-points">Part 3 (SSMS &amp; SQL) - 40 points</h2>
<p>Use the BikeStores database for these exercises.</p>
<ol>
<li>What tables exist in the database?  Identify them as either coming from the production schema or the sales schema.</li>
<li>How many columns exist in the staff table and what are the data types and do they allow nulls or not?</li>
<li>Take a look at the <a href="https://image2url.com/r2/default/images/1769997410862-103e7cf9-6c15-4767-a888-6aeff139b1e1.png">diagram</a> for the database.</li>
</ol>
<ul>
<li>Identify any relationships that are recursive.</li>
<li>Identify any tables that serve as bridging tables between two entities where a M:N would exist.</li>
<li>Is orders a weak or strong entity in your opinion?  Justify your response, but do not use the lines or rectangle in doing so.  I will accept either answer with appropriate justification.</li>
<li>If we wanted to see shipped_date along with brand_name, how many joins would be required?  List two different paths and how many joins for each path.</li>
</ul>
<ol start="4">
<li>Answer the following by writing an appropriate database query:</li>
</ol>
<ul>
<li>How many customers do we have phone numbers on file for?</li>
<li>How many customers does Baldwin Bikes have?</li>
<li>Which store stocks the most brands and how many? (Use Top 1 and Order By)</li>
<li>What’s the cheapest product each brand sells?</li>
<li>What is the most expensive product from each category in each year?  (The specific product name isn’t required.)</li>
<li>Which staff members have sold to at least 3 customers?</li>
<li>What is the average list price per brand?</li>
<li>What is the total quantity purchased by each customer over their lifetime?</li>
<li>Bonus: Which 5 customers (first + last) have the lowest average per order amounts?  Take into account that they pay the list minus the discount on each item they purchase.  You should use a subquery for this one.</li>
</ul>
<p>Here’s a sample to get you started that instead finds the top 10 customers with the highest average number of items per order, requiring that they have more than 2 orders.</p>
<pre><code>SELECT TOP 10
    c.first_name, 
    c.last_name, 
    AVG(OrderCounts.ItemsInBox) AS AvgItemsPerOrder
FROM sales.customers c
JOIN (
    -- Subquery for counting total items for every individual order
    SELECT o.customer_id, o.order_id, SUM(oi.quantity) AS ItemsInBox
    FROM sales.orders o
    JOIN sales.order_items oi ON o.order_id = oi.order_id
    GROUP BY o.customer_id, o.order_id
) AS OrderCounts ON c.customer_id = OrderCounts.customer_id
GROUP BY c.customer_id, c.first_name, c.last_name
HAVING COUNT(OrderCounts.order_id) &gt; 2
ORDER BY AvgItemsPerOrder DESC;
</code></pre>
<ol start="6">
<li>Ask 5 questions of your own and write a database query to answer them.  The requirements:</li>
</ol>
<ul>
<li>At least 3 require joins.</li>
<li>At least 3 require the use of either sum, avg, count, min, or max.</li>
<li>At least 2 require groupby and/or having.</li>
</ul>
<blockquote>
<p>Written with <a href="https://stackedit.io/">StackEdit</a>.</p>
</blockquote>

