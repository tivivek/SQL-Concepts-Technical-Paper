---


---

<h1 id="some-concepts-to-understand-for-databases">Some concepts to understand for databases:</h1>
<h2 id="acid-atomicity-consistency-isolation-durability">ACID (Atomicity, Consistency, Isolation, Durability)</h2>
<p>ACID  is a set of four key properties that gurantees reliable processing of database transactions. If a databse operation has these four properties <strong>Atomicity</strong>, <strong>Consistency</strong>, <strong>Isolation</strong> and <strong>Durability</strong>,  it can be called an ACID transaction. These properties are essential to ensure data integrity and reliablity, especially in mission critical systems. ACID transactions guarantee that each read, write, or modification of a table has the following properties:</p>
<ul>
<li>
<p><strong>Atomicity</strong> - each statement in a transaction is treated as a single, indivisible unit. It means either entire statement is executed or none of them. It prevents data loss and corruption from occurring if, for example, if your streaming data source fails mid-stream. If any part of the transaction fails, the entire transaction is rolled back to its previous state.</p>
</li>
<li>
<p><strong>Consistency</strong> - It ensures that transactions only make changes to tables in predefined, predictable ways. Transactional consistency ensures that corruption or errors in your data do not create unintended consequences for the integrity of your table. The database must satisfy all integrity constraints, such as referential integrity and unique key constraints, before and after the transaction.</p>
</li>
<li>
<p><strong>Isolation</strong> - Isolation ensures that concurrent transactions do not interfere with each other. Each transaction must appear as if it is the only transaction executing, even when multiple transactions are running concurrently. Isolation levels (e.g., Read Uncommitted, Read Committed, Repeatable Read, Serializable) control the level of isolation.</p>
</li>
<li>
<p><strong>Durability</strong> - It guarantees that once a transaction is committed, its effects are permanent and survive system failures. This is typically achieved by writing transaction changes to durable storage, such as disk, and ensuring they can be recovered in case of a crash.</p>
</li>
</ul>
<p>ACID properties are vital for maintaining data integrity and consistency, making them a cornerstone of relational database management systems (RDBMS).</p>
<h2 id="cap-theorem-consistency-availability-partition-tolerance">CAP Theorem (Consistency, Availability, Partition Tolerance)</h2>
<p>The CAP theorem applies a type of logic to distributed systems, that a distributed system can deliver only two of three desired characteristics: <em><strong>consistency</strong>,  <strong>availability</strong>,</em> and <em><strong>partition tolerance</strong></em> (the ‘<strong>C</strong>,’ ‘<strong>A</strong>’ and ‘<strong>P</strong>’ in CAP).</p>
<p>The CAP theorem is also called Brewer’s Theorem, because it was first advanced by Professor Eric A. Brewer during a talk he gave on distributed computing in 2000. Two years later, MIT professors Seth Gilbert and Nancy Lynch published a proof of “Brewer’s Conjecture.”</p>
<ul>
<li>
<p><strong>Consistency</strong> - It means that all clients see the same data at the same time, no matter which node they connect to. For this to happen, whenever data is written to one node, it must be instantly forwarded or replicated to all the other nodes in the system before the write is deemed ‘successful.’</p>
</li>
<li>
<p><strong>Availability</strong> - Availability means that any client making a request for data gets a response, even if one or more nodes are down. Another way to state this—all working nodes in the distributed system return a valid response for any request, without exception.</p>
</li>
<li>
<p><strong>Partition tolerance</strong> - A partition is a communications break within a distributed system—a lost or temporarily delayed connection between two nodes. Partition tolerance means that the cluster must continue to work despite any number of communication breakdowns between nodes in the system.</p>
</li>
</ul>
<p>According to the CAP theorem, a distributed system can only guarantee two out of the three properties simultaneously. For example:</p>
<ul>
<li>
<p><strong>CA</strong>: A system that prioritizes Consistency and Availability may not tolerate network partitions and can become unavailable during a partition.</p>
</li>
<li>
<p><strong>CP</strong>: A system that prioritizes Consistency and Partition Tolerance may sacrifice Availability during network partitions.</p>
</li>
<li>
<p><strong>AP</strong>: A system that prioritizes Availability and Partition Tolerance may provide eventual consistency but may not guarantee immediate consistency.</p>
</li>
</ul>
<h2 id="joins">Joins</h2>
<p>The join clause allows us to  <strong>retrieve data from two or more related tables</strong>  into a meaningful result set. We can join the table using a  <strong>SELECT</strong>  statement and a  <strong>join condition</strong>. It indicates how SQL Server can use data from one table to select rows from another table. In general, tables are related to each other using  <strong>foreign key</strong>  constraints.</p>
<p>In a JOIN query, a condition indicates how two tables are related:</p>
<ul>
<li>Choose columns from each table that should be used in the join. A join condition indicates a foreign key from one table and its corresponding key in the other table.</li>
<li>Specify the logical operator to compare values from the columns like =, &lt;, or &gt;.</li>
</ul>
<h3 id="types-of-joins-in-sql-server">Types of JOINS in SQL Server</h3>
<ol>
<li><strong>INNER JOIN</strong>: This JOIN returns all records from multiple tables that satisfy the specified join condition. It is the simple and most popular form of join and assumes as a <strong>default join</strong>. If we omit the INNER keyword with the JOIN query, we will get the same output.</li>
<li><strong>LEFT JOIN (or LEFT OUTER JOIN)</strong>: Returns all rows from the left table and the matched rows from the right table. If there is no match, NULL values are returned for right table columns.</li>
<li><strong>RIGHT JOIN (or RIGHT OUTER JOIN)</strong>: Similar to LEFT JOIN but returns all rows from the right table.</li>
<li><strong>FULL JOIN (or FULL OUTER JOIN)</strong>: Returns all rows when there is a match in either the left or right table. NULL values are returned for non-matching rows.</li>
<li><strong>SELF JOIN</strong>: Joins a table with itself to combine rows based on a related column within the same table.</li>
</ol>
<p>Joins are crucial for querying and retrieving data from multiple related tables in a relational database. They enable complex data retrieval and analysis.</p>
<h2 id="aggregations-and-filters-in-queries">Aggregations and Filters in Queries</h2>
<p>Aggregations and filters are SQL operations that allow you to summarize data and retrieve specific subsets of data from a database:</p>
<ol>
<li>
<p><strong>Aggregations</strong>: Aggregation functions like SUM, AVG, COUNT, MIN, and MAX are used to perform calculations on groups of rows. For example, you can calculate the total sales, average price, or count of products in a category.</p>
</li>
<li>
<p><strong>Filters</strong>: Filters, specified using the WHERE clause, allow you to select rows that meet specific criteria. For instance, you can filter orders placed within a certain date range or customers from a particular location.</p>
</li>
</ol>
<p>These operations are essential for generating meaningful insights from large datasets and extracting relevant information.</p>
<h2 id="normalization">Normalization</h2>
<p>Normalization is a database design technique used to minimize data redundancy and improve data integrity by organizing data into separate tables and defining relationships between them. It involves breaking down large tables into smaller, related tables and using foreign keys to establish relationships. The primary goals of normalization are:</p>
<ol>
<li>
<p>Eliminating data redundancy: Storing data in a single place reduces the risk of inconsistencies and errors.</p>
</li>
<li>
<p>Reducing update anomalies: Normalization ensures that updates or modifications to the database do not result in unintended consequences, such as data inconsistencies.</p>
</li>
</ol>
<p>Normalization follows a set of normalization forms, with the most common ones being First Normal Form (1NF), Second Normal Form (2NF), and Third Normal Form (3NF). Each form has specific rules that guide the process of breaking down tables and defining relationships.</p>
<p>Normalization is a key practice for maintaining data integrity and ensuring efficient database operations.</p>
<h2 id="indexes">Indexes</h2>
<p>Indexes are data structures that provide rapid access to rows in a database table. They work similarly to the index in a book, allowing the database management system to quickly locate specific rows without scanning the entire table. Key points about indexes include:</p>
<ol>
<li>
<p><strong>Types of Indexes</strong>: Common types of indexes include B-tree, Hash, and Bitmap indexes. B-tree indexes are most commonly used in relational databases.</p>
</li>
<li>
<p><strong>Column Indexing</strong>: Indexes can be created on one or more columns of a table to accelerate data retrieval for queries involving those columns.</p>
</li>
<li>
<p><strong>Performance Impact</strong>: Indexes improve query performance for SELECT statements but may slightly slow down data modification operations (INSERT, UPDATE, DELETE) because the index structures need to be maintained.</p>
</li>
<li>
<p><strong>Index Selection</strong>: Choosing the right columns to index is crucial. Over-indexing or indexing the wrong columns can lead to decreased performance and increased storage requirements.</p>
</li>
</ol>
<p>Indexes play a pivotal role in optimizing database performance by reducing query execution time, especially for large datasets.</p>
<h2 id="transactions">Transactions</h2>
<p><strong>Transactions</strong> represent a fundamental unit of work within a database system. They are used to group one or more SQL operations into a single, indivisible unit. The properties of a transaction are often summarized by the acronym ACID (Atomicity, Consistency, Isolation, Durability), as discussed in the previous section.</p>
<p>Transactions ensure data integrity and reliability in multi-user database environments, making them a crucial concept in RDBMS.</p>
<h2 id="locking-mechanism">Locking Mechanism</h2>
<p><strong>Locking Mechanism</strong> is a fundamental concept for managing concurrent access to data in a database. In multi-user environments, multiple transactions may attempt to access and modify the same data simultaneously, potentially leading to conflicts and data inconsistencies.</p>
<p>Locking is essential to successful SQL Server transactions processing and it is designed to allow SQL Server to work seamlessly in a multi-user environment. Locking is the way that SQL Server manages transaction concurrency. Essentially, locks are in-memory structures which have owners, types, and the hash of the resource that it should protect. A lock as an in-memory structure is 96 bytes in size.</p>
<p>To understand better the locking in SQL Server, it is important to understand that locking is designed to ensure the integrity of the data in the database, as it forces every SQL Server transaction to pass the ACID test.</p>
<p>SQL Server locking is the essential part of the isolation requirement and it serves to lock the objects affected by a transaction. While objects are locked, SQL Server will prevent other transactions from making any change of data stored in objects affected by the imposed lock. Once the lock is released by committing the changes or by rolling back changes to initial state, other transactions will be allowed to make required data changes.</p>
<p>Translated into the SQL Server language, this means that when a transaction imposes the lock on an object, all other transactions that require the access to that object will be forced to wait until the lock is released and that wait will be registered with the adequate wait type</p>
<p>SQL Server locks can be specified via the lock modes and lock granularity</p>
<ol>
<li>
<p><strong>Types of Locks</strong>: There are various types of locks, including shared locks (read locks) and exclusive locks (write locks). Shared locks allow multiple transactions to read data concurrently but prevent write access. Exclusive locks grant exclusive write access, blocking other transactions from reading or writing to the locked data.</p>
</li>
<li>
<p><strong>Concurrency Control</strong>: Locking mechanisms help enforce concurrency control by ensuring that only one transaction can modify a piece of data at a time. This prevents issues like the “lost update” problem, where one transaction’s changes may overwrite another’s.</p>
</li>
<li>
<p><strong>Deadlocks</strong>: Deadlocks can occur when transactions lock resources and wait indefinitely for each other to release their locks. Database management systems often include deadlock detection and resolution mechanisms to address this issue.</p>
</li>
</ol>
<p>Locking mechanisms are essential for maintaining data consistency and preventing conflicts in multi-user database systems.</p>
<h2 id="database-isolation-levels">Database Isolation Levels</h2>
<p><strong>Database Isolation Levels</strong> define the level of isolation and concurrency control between transactions. Different isolation levels provide varying degrees of data consistency and concurrency while balancing performance and reliability. The most common isolation levels include:</p>
<ol>
<li>
<p><strong>Read Uncommitted</strong>: Transactions can read uncommitted changes made by other transactions. This level offers maximum concurrency but the lowest data consistency.</p>
</li>
<li>
<p><strong>Read Committed</strong>: Transactions can only read committed changes, ensuring a higher level of data consistency. However, it may still allow non-repeatable reads.</p>
</li>
<li>
<p><strong>Repeatable Read</strong>: Transactions are isolated from other transactions, preventing non-repeatable reads. However, it may allow phantom reads (new rows matching the query appearing).</p>
</li>
<li>
<p><strong>Serializable</strong>: Provides the highest level of isolation by ensuring that transactions execute as if they were executed sequentially, preventing any anomalies. It offers the highest data consistency but may impact concurrency.</p>
</li>
</ol>
<p>Database administrators must carefully select the appropriate isolation level based on the application’s requirements to balance data consistency and concurrency.</p>
<h2 id="triggers">Triggers</h2>
<p><strong>Triggers</strong> are database objects that automatically execute a set of actions (SQL statements) in response to specific events or conditions. Triggers are often used for:</p>
<ol>
<li>
<p><strong>Data Validation</strong>: Ensuring that data entering the database meets specific criteria or constraints.</p>
</li>
<li>
<p><strong>Logging</strong>: Capturing changes made to specific tables for audit purposes.</p>
</li>
<li>
<p><strong>Automated Actions</strong>: Executing predefined actions when certain events occur, such as sending email notifications when a new record is inserted.</p>
</li>
<li>
<p><strong>Referential Integrity</strong>: Enforcing referential integrity by automatically updating or deleting related records when changes are made to primary key values.</p>
</li>
</ol>
<p>Triggers can be “before” triggers (executed before the event) or “after” triggers (executed after the event). They provide a powerful mechanism for automating actions and maintaining data integrity within the database.</p>

