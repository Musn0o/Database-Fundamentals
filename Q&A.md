### SQL / Database (Very Important topic)

#### DDL, DML, DCL

*   Q01 - What are DCL, DML, and DDL in SQL?
    *   **A01:**
        *   **DDL (Data Definition Language):** Deals with the schema and descriptions of how the data is managed in the database. Commands include `CREATE`, `ALTER`, `DROP`, `TRUNCATE`, `RENAME`.
        *   **DML (Data Manipulation Language):** Deals with the manipulation of data within the database. Commands include `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
        *   **DCL (Data Control Language):** Deals with the rights, permissions, and other controls of the database system. Commands include `GRANT`, `REVOKE`.

#### SELECT Statement Clauses

*   Q02 - What is the difference between group by and having?
    *   **A02:**
        *   **`GROUP BY` Clause:** Used to group rows that have the same values in specified columns into a summary row. It operates on individual rows before aggregation.
        *   **`HAVING` Clause:** Used to filter groups based on specified conditions. It operates on aggregated data, after the `GROUP BY` clause has grouped the rows.

*   Q03 - What is order by? Can we order more than one column?
    *   **A03:**
        *   **`ORDER BY` Clause:** Used to sort the result-set of a query in ascending (ASC) or descending (DESC) order based on one or more columns.
        *   **Ordering Multiple Columns:** Yes, you can order by more than one column. The sorting is applied sequentially; if the first column has identical values, the second column's sort order is applied to those rows, and so on.

*   Q04 - What is the order of execution for clauses in a SQL SELECT statement?
    *   **A04:** The logical order of execution for clauses in a SQL `SELECT` statement is:
        1.  `FROM` (and `JOIN`s)
        2.  `WHERE`
        3.  `GROUP BY`
        4.  `HAVING`
        5.  `SELECT`
        6.  `DISTINCT`
        7.  `ORDER BY`
        8.  `LIMIT`/`OFFSET` (or `TOP`)

*   Q05 - What is the difference between Where and Having?
    *   **A05:**
        *   **`WHERE` Clause:** Filters individual rows *before* they are grouped. It cannot contain aggregate functions.
        *   **`HAVING` Clause:** Filters groups of rows *after* they have been grouped by the `GROUP BY` clause. It can contain aggregate functions.

*   Q06 - What is the difference between Group by and Order By?
    *   **A06:**
        *   **`GROUP BY` Clause:** Groups rows that have the same values in specified columns into a summary row. It's used for aggregation.
        *   **`ORDER BY` Clause:** Sorts the final result set based on specified columns. It's used for presentation.

*   Q07 - Between HAVING and GROUP BY, which one is mandatory or a prerequisite for the other?
    *   **A07:** The `GROUP BY` clause is a prerequisite for the `HAVING` clause. You cannot use `HAVING` without a `GROUP BY` clause, because `HAVING` filters groups, and groups are created by `GROUP BY`.

#### JOINs and UNION

*   Q08 - What is the difference between union and join?
    *   **A08:**
        *   **`UNION` Operator:** Combines the result-set of two or more `SELECT` statements. All `SELECT` statements must have the same number of columns, the columns must have similar data types, and the columns must be in the same order. `UNION` removes duplicate rows by default (`UNION ALL` includes duplicates). It combines rows vertically.
        *   **`JOIN` Clause:** Combines rows from two or more tables based on a related column between them. It combines columns horizontally. Different types of joins (INNER, LEFT, RIGHT, FULL) determine how rows are matched and included.

*   Q09 - What are the different types of joins?
    *   **A09:** The main types of joins in SQL are:
        *   **`INNER JOIN`:** Returns only the rows that have matching values in both tables.
        *   **`LEFT JOIN` (or `LEFT OUTER JOIN`):** Returns all rows from the left table, and the matching rows from the right table. If there is no match in the right table, `NULL` values are returned for columns from the right table.
        *   **`RIGHT JOIN` (or `RIGHT OUTER JOIN`):** Returns all rows from the right table, and the matching rows from the left table. If there is no match in the left table, `NULL` values are returned for columns from the left table.
        *   **`FULL JOIN` (or `FULL OUTER JOIN`):** Returns all rows when there is a match in one of the tables. If there are rows in one table that do not have matches in the other, `NULL` values are returned for columns from the non-matching side.
        *   **`CROSS JOIN`:** Returns the Cartesian product of the rows from the joined tables. It combines each row from the first table with every row from the second table.

*   Q10 - What is the difference between inner join and union?
    *   **A10:**
        *   **`INNER JOIN`:** Combines columns from two tables horizontally based on a matching condition. It returns only the rows where there is a match in *both* tables.
        *   **`UNION`:** Combines rows from two or more `SELECT` statements vertically. It requires the same number and order of columns with compatible data types.

*   Q11 - What is a self-join
    *   **A11:** A self-join is a join in which a table is joined with itself. This is useful when you need to compare rows within the same table, such as finding employees who report to the same manager, or finding pairs of products that are frequently bought together. Aliases are typically used to distinguish between the two instances of the table.

#### Functions and Views

*   Q12 - What are the aggregate functions?
    *   **A12:** Aggregate functions perform a calculation on a set of rows and return a single summary value. Common SQL aggregate functions include:
        *   `COUNT()`: Returns the number of rows that match a specified criterion.
        *   `SUM()`: Calculates the sum of a set of values.
        *   `AVG()`: Calculates the average of a set of values.
        *   `MIN()`: Returns the minimum value in a set.
        *   `MAX()`: Returns the maximum value in a set.

*   Q13 - What is the view? Why do we use it?
    *   **A13:**
        *   **View:** A virtual table based on the result-set of a SQL query. A view contains rows and columns, just like a real table, but it does not store data itself. The data is stored in the underlying tables.
        *   **Reasons to use views:**
            *   **Security:** Restrict access to certain rows or columns of a table.
            *   **Simplicity:** Simplify complex queries by pre-joining tables or pre-aggregating data.
            *   **Consistency:** Present a consistent, unchanging view of data even if the underlying schema changes.
            *   **Logical Data Independence:** Provide a layer of abstraction between the user and the base tables.

*   Q14 - What are the types of views?
    *   **A14:** Views can generally be categorized into:
        *   **Simple View:** Based on a single table, does not contain aggregate functions, `GROUP BY`, `DISTINCT`, or subqueries. Can be used for DML operations (INSERT, UPDATE, DELETE) on the underlying table.
        *   **Complex View:** Based on multiple tables, or contains aggregate functions, `GROUP BY`, `DISTINCT`, or subqueries. Typically, DML operations are not allowed on complex views.
        *   **Materialized View (or Indexed View/Snapshot):** A physical copy of the query result stored on disk. Unlike a regular view, a materialized view stores the data and can be refreshed periodically. They are used to improve query performance, especially for complex queries or data warehousing.  

#### Data Manipulation

*   Q15 - What is the difference between delete and truncate?
    *   **A15:**
        *   **`DELETE` Statement:**
            *   A DML (Data Manipulation Language) command.
            *   Removes rows one by one.
            *   Can be used with a `WHERE` clause to remove specific rows.
            *   Generates rollback information, so the operation can be rolled back.
            *   Fires triggers.
            *   Slower for large tables as it logs each row deletion.
        *   **`TRUNCATE` Statement:**
            *   A DDL (Data Definition Language) command.
            *   Removes all rows from a table by deallocating the data pages used by the table.
            *   Cannot be used with a `WHERE` clause.
            *   Does not generate rollback information (or generates minimal), so it cannot be rolled back.
            *   Does not fire triggers.
            *   Faster for large tables as it's a logged operation that deallocates data pages. Resets identity columns.

*   Q16 - How can you add a column to a table?
    *   **A16:** You can add a column to an existing table using the `ALTER TABLE` statement with the `ADD COLUMN` clause.
        **Syntax:**
        ```sql
        ALTER TABLE table_name
        ADD COLUMN column_name datatype [constraints];
        ```
        **Example:**
        ```sql
        ALTER TABLE Employees
        ADD COLUMN Email VARCHAR(100);
        ```

*   Q17 - How can you insert multiple rows in a single INSERT statement?
    *   **A17:** You can insert multiple rows in a single `INSERT` statement by providing multiple sets of values, separated by commas, after the `VALUES` keyword.
        **Syntax:**
        ```sql
        INSERT INTO table_name (column1, column2, column3)
        VALUES
            (value1_row1, value2_row1, value3_row1),
            (value1_row2, value2_row2, value3_row2),
            (value1_row3, value2_row3, value3_row3);
        ```
        **Example:**
        ```sql
        INSERT INTO Products (ProductName, Price, Stock)
        VALUES
            ('Laptop', 1200.00, 50),
            ('Mouse', 25.00, 200),
            ('Keyboard', 75.00, 150);
        ```

*   Q18 - What is delete set null and delete cascade?
    *   **A18:** These are actions defined for foreign key constraints, specifying what happens to child records when a parent record is deleted.
        *   **`ON DELETE SET NULL`:** When a row in the parent table is deleted, the foreign key values in the matching child rows are set to `NULL`. This requires the foreign key column in the child table to be nullable.
        *   **`ON DELETE CASCADE`:** When a row in the parent table is deleted, the matching rows in the child table are automatically deleted. This propagates the deletion from the parent to the child table.

*   Q19 - What is the difference between Delete and Drop?
    *   **A19:**
        *   **`DELETE` Statement:**
            *   A DML (Data Manipulation Language) command.
            *   Removes rows from a table.
            *   Keeps the table structure (schema), indexes, and constraints.
            *   Can be rolled back.
        *   **`DROP` Statement:**
            *   A DDL (Data Definition Language) command.
            *   Removes an entire database object (e.g., table, index, view, database) from the database.
            *   Deletes the table structure, data, indexes, and constraints permanently.
            *   Cannot be rolled back.

*   Q20 - Which is faster: DELETE or TRUNCATE?
    *   **A20:** `TRUNCATE` is generally faster than `DELETE` for removing all rows from a table.
        *   **`TRUNCATE`** is a DDL command that deallocates the data pages used by the table, making it a very efficient operation, especially for large tables. It performs minimal logging.
        *   **`DELETE`** is a DML command that removes rows one by one, logging each deletion. This makes it slower, especially for large tables, but it allows for rollback and can be used with a `WHERE` clause.

#### Database Concepts

*   Q21 - What are a database, DBMS, and RDBMS?
    *   **A21:**
        *   **Database:** An organized collection of structured information, or data, typically stored electronically in a computer system. It's designed to efficiently store, retrieve, and manage data.
        *   **DBMS (Database Management System):** Software that interacts with end-users, applications, and the database itself to capture and analyze data. A DBMS provides a systematic way to create, retrieve, update, and manage data. Examples: MySQL, PostgreSQL, MongoDB.
        *   **RDBMS (Relational Database Management System):** A type of DBMS that stores data in a structured format of rows and columns, known as tables. Data is organized into relations (tables) and relationships between these tables are established using primary and foreign keys. Examples: MySQL, PostgreSQL, Oracle, SQL Server.

*   Q22 - What are the kinds of attributes?
    *   **A22:** In the context of databases (especially ER modeling), attributes describe the properties or characteristics of an entity. Common kinds of attributes include:
        *   **Simple Attribute:** Cannot be further divided (e.g., `Age`, `Gender`).
        *   **Composite Attribute:** Can be divided into smaller sub-parts (e.g., `Address` can be divided into `Street`, `City`, `State`, `Zip Code`).
        *   **Single-valued Attribute:** Holds a single value for a particular entity (e.g., `EmployeeID`).
        *   **Multi-valued Attribute:** Can hold multiple values for a particular entity (e.g., `Phone Number` for a person who has multiple phones).
        *   **Derived Attribute:** An attribute whose value can be derived from other attributes (e.g., `Age` can be derived from `Date of Birth`).
        *   **Key Attribute:** An attribute (or set of attributes) that uniquely identifies an entity in an entity set (e.g., `StudentID`).

*   Q23 - What is the ERD?
    *   **A23:**
        *   **ERD (Entity-Relationship Diagram):** A visual representation of the relationships between entities (things or objects) in a database. It's a high-level data model that helps in designing a database by illustrating how different entities are related to each other.
        *   **Components of an ERD:**
            *   **Entities:** Represented by rectangles (e.g., `Student`, `Course`).
            *   **Attributes:** Represented by ovals, connected to entities (e.g., `StudentID`, `CourseName`).
            *   **Relationships:** Represented by diamonds, connecting entities (e.g., `enrolls in`).

*   Q24 - What is an Entity ?
    *   **A24:** In the context of a database, an entity is a real-world object or concept that is distinguishable from other objects and has properties (attributes) that describe it. It can be a person, place, thing, event, or concept about which data is stored. Examples include a `Student`, a `Book`, a `Car`, or an `Order`.

*   Q25 - What is Weak Entity ?
    *   **A25:** A weak entity is an entity that cannot be uniquely identified by its own attributes alone. It depends on another entity (called the identifying or owner entity) for its existence and for the formation of its primary key. The primary key of a weak entity is formed by a combination of its partial key and the primary key of its identifying entity. Example: A `Dependent` entity might be weak if its existence and unique identification depend on an `Employee` entity.

*   Q26 - What are the types of databases?
    *   **A26:** Databases can be categorized in various ways, including:
        *   **Relational Databases (SQL Databases):** Store data in tables with rows and columns, using SQL for data manipulation. (e.g., MySQL, PostgreSQL, Oracle, SQL Server)
        *   **NoSQL Databases:** Non-relational databases that provide flexible schemas and are designed for specific data models. (e.g., MongoDB (Document), Cassandra (Column-family), Redis (Key-value), Neo4j (Graph))
        *   **Cloud Databases:** Databases built and accessed through a cloud platform. (e.g., Amazon RDS, Google Cloud SQL, Azure SQL Database)
        *   **Object-Oriented Databases:** Store data as objects, similar to object-oriented programming.
        *   **Hierarchical Databases:** Organize data in a tree-like structure.
        *   **Network Databases:** More flexible than hierarchical, allowing multiple parent-child relationships.

*   Q27 - What is cardinality in a database?
    *   **A27:** Cardinality in a database refers to the uniqueness of data values contained in a column. It describes the number of unique values in a column relative to the total number of rows in the table.
        *   **High Cardinality:** A column has high cardinality if it contains a large percentage of unique values (e.g., `Social Security Number`, `Email Address`).
        *   **Low Cardinality:** A column has low cardinality if it contains a small percentage of unique values (e.g., `Gender`, `True/False` flags).
        *   **Cardinality in Relationships:** Also refers to the number of instances of one entity that can be associated with the number of instances of another entity in a relationship (e.g., one-to-one, one-to-many, many-to-many).

#### Constraints

*   Q28 - What are the types of constraints?
    *   **A28:** Constraints are rules enforced on data columns in a table to limit the type of data that can be inserted or updated. This ensures the accuracy and reliability of the data in the database. Common types of constraints include:
        *   **`NOT NULL`:** Ensures that a column cannot have a `NULL` value.
        *   **`UNIQUE`:** Ensures that all values in a column are different.
        *   **`PRIMARY KEY`:** A combination of `NOT NULL` and `UNIQUE`. Uniquely identifies each row in a table. A table can have only one primary key.
        *   **`FOREIGN KEY`:** A key used to link two tables together. It refers to the primary key in another table.
        *   **`CHECK`:** Ensures that all values in a column satisfy a specific condition.
        *   **`DEFAULT`:** Provides a default value for a column when no value is specified.

*   Q29 - What is the difference between primary key and foreign key?
    *   **A29:**
        *   **`PRIMARY KEY`:**
            *   Uniquely identifies each record in a table.
            *   Cannot contain `NULL` values.
            *   Must contain unique values.
            *   A table can have only one primary key.
        *   **`FOREIGN KEY`:**
            *   A field (or collection of fields) in one table that refers to the `PRIMARY KEY` in another table.
            *   Establishes a link or relationship between two tables.
            *   Can contain `NULL` values (unless `NOT NULL` constraint is also applied).
            *   Can contain duplicate values.
            *   A table can have multiple foreign keys.

*   Q30 - Define constraints in SQL.
    *   **A30:** In SQL, constraints are rules that are enforced on the data columns of a table. They are used to limit the type of data that can go into a table, ensuring the accuracy and integrity of the data. Constraints can be column-level (applied to a single column) or table-level (applied to the whole table).

*   Q31 - What is the difference between primary key, unique key, and foreign key?
    *   **A31:**
        *   **`PRIMARY KEY`:** Uniquely identifies each record in a table. It enforces both `UNIQUE` and `NOT NULL` constraints. A table can have only one primary key.
        *   **`UNIQUE KEY`:** Ensures that all values in a column (or set of columns) are unique. It allows `NULL` values (only one `NULL` value is allowed per `UNIQUE` column). A table can have multiple unique keys.
        *   **`FOREIGN KEY`:** A field in one table that refers to the `PRIMARY KEY` (or `UNIQUE KEY`) in another table. It establishes a link between tables and enforces referential integrity.

*   Q32 - What is the difference between NULL and NOT NULL?
    *   **A32:**
        *   **`NULL`:** Represents a missing or unknown value in a column. It is not the same as an empty string or zero.
        *   **`NOT NULL`:** A constraint that ensures a column cannot have a `NULL` value. If this constraint is applied, every row in that column must have a value.

*   Q33 - What is a CHECK constraint in SQL?
    *   **A33:** A `CHECK` constraint is used to limit the range of values that can be placed in a column. It ensures that all values in a column satisfy a specific condition. For example, you could use a `CHECK` constraint to ensure that the `Age` column only contains values greater than 0.

*   Q34 - What is a DEFAULT constraint in SQL?
    *   **A34:** A `DEFAULT` constraint is used to provide a default value for a column when no value is specified during an `INSERT` operation. If no other value is provided, the default value will be automatically inserted into the column.

#### Normalization

*   Q35 - What is normalization and why is it used?
    *   **A35:**
        *   **Normalization:** The process of organizing the columns and tables of a relational database to minimize data redundancy and improve data integrity. It involves breaking down a large table into smaller, related tables and defining relationships between them.
        *   **Why it is used:**
            *   **Reduce Data Redundancy:** Avoids storing the same data multiple times, saving storage space and preventing inconsistencies.
            *   **Improve Data Integrity:** Ensures that data is accurate and consistent across the database.
            *   **Eliminate Anomalies:** Helps to avoid insertion, update, and deletion anomalies.
            *   **Better Database Design:** Leads to a more organized, flexible, and maintainable database structure.

*   Q36 - What are the types of normalization?
    *   **A36:** Normalization is typically performed in stages, called normal forms. The most common normal forms are:
        *   **First Normal Form (1NF):**
            *   Each column contains atomic (indivisible) values.
            *   There are no repeating groups of columns.
        *   **Second Normal Form (2NF):**
            *   Must be in 1NF.
            *   All non-key attributes are fully functionally dependent on the primary key (i.e., no partial dependencies).
        *   **Third Normal Form (3NF):**
            *   Must be in 2NF.
            *   No transitive dependencies (i.e., no non-key attribute is dependent on another non-key attribute).
        *   **Boyce-Codd Normal Form (BCNF):**
            *   A stricter version of 3NF.
            *   Every determinant (attribute that determines other attributes) must be a candidate key.
        *   **Fourth Normal Form (4NF):
            *   Must be in BCNF.
            *   No multi-valued dependencies.
        *   **Fifth Normal Form (5NF):
            *   Must be in 4NF.
            *   No join dependencies.

*   Q37 - What are the update anomalies?
    *   **A37:** Update anomalies are problems that can occur in poorly designed (unnormalized) databases when data is redundant. There are three main types:
        *   **Insertion Anomaly:** Occurs when you cannot insert a new record into the database without adding information about another entity that may not yet exist. For example, you can't add a new course without assigning a student to it.
        *   **Deletion Anomaly:** Occurs when deleting a record unintentionally removes other important information. For example, deleting the last student enrolled in a course might also delete all information about that course.
        *   **Update Anomaly:** Occurs when the same information is stored in multiple places, and updating one instance of the data leaves other instances inconsistent. For example, if a student's address is stored in multiple tables, and it's updated in one table but not others, data inconsistency arises.

*   Q38 - What is denormalization?
    *   **A38:** Denormalization is the process of intentionally introducing redundancy into a database schema, often by combining tables or adding duplicate data. This is typically done to improve query performance, especially in data warehousing or reporting systems, where read operations are more frequent than write operations. While it sacrifices some data integrity and increases redundancy, it can significantly reduce the number of joins required for queries, leading to faster data retrieval.

#### PL/SQL

*   Q39 - What is the difference between SQL and PL/SQL?
    *   **A39:**
        *   **SQL (Structured Query Language):**
            *   A declarative language used to manage and manipulate data in relational databases.
            *   Primarily used for querying, inserting, updating, and deleting data.
            *   Executes one statement at a time.
            *   Does not support procedural programming constructs like loops, conditional statements, or variables (beyond basic query variables).
        *   **PL/SQL (Procedural Language/SQL):**
            *   A procedural extension to SQL, developed by Oracle.
            *   Combines the data manipulation capabilities of SQL with the procedural programming features of a traditional programming language.
            *   Allows for the use of variables, conditional statements (`IF-THEN-ELSE`), loops (`FOR`, `WHILE`), and error handling.
            *   Used to create stored procedures, functions, triggers, and packages.
            *   Executes blocks of code, which can contain multiple SQL statements.

*   Q40 - What are the types of loops in PL/SQL?
    *   **A40:** PL/SQL supports several types of loops to execute a block of code repeatedly:
        *   **`LOOP...END LOOP` (Basic Loop):** The simplest form of loop. It executes statements repeatedly until an `EXIT` or `EXIT WHEN` statement is encountered.
        *   **`WHILE-LOOP`:** Executes statements repeatedly as long as a specified condition is true. The condition is evaluated at the beginning of each iteration.
        *   **`FOR-LOOP` (Numeric FOR Loop):** Executes statements a fixed number of times. It's ideal when you know the number of iterations in advance.
        *   **`FOR-LOOP` (Cursor FOR Loop):** Iterates through each row returned by a SQL query (cursor). It implicitly opens, fetches from, and closes the cursor.

*   Q41 - What are cursors and what are their types?
    *   **A41:**
        *   **Cursor:** A pointer or a control structure that enables traversal over the records in a database. It allows you to process individual rows returned by a `SELECT` statement, rather than processing the entire result set at once.
        *   **Types of Cursors:**
            *   **Implicit Cursors:** Automatically created and managed by the database system for all DML statements (`INSERT`, `UPDATE`, `DELETE`) and single-row `SELECT` statements. You don't explicitly declare or manage them.
            *   **Explicit Cursors:** Declared and managed by the programmer for `SELECT` statements that return multiple rows. They require explicit steps: `DECLARE`, `OPEN`, `FETCH`, and `CLOSE`.

*   Q42 - What is a procedure?
    *   **A42:** A procedure (or stored procedure) is a named PL/SQL block that performs a specific task. It is stored in the database and can be executed multiple times by different applications or users. Procedures can accept input parameters and return output parameters, but they do not return a value directly like functions. They are primarily used for performing DML operations or complex business logic.

*   Q43 - What is the difference between a procedure and a function?
    *   **A43:**
        *   **Procedure:**
            *   Does not return a value directly (can return values via `OUT` parameters).
            *   Can perform DML operations (`INSERT`, `UPDATE`, `DELETE`).
            *   Can be called as a SQL statement.
            *   Primarily used for performing actions or complex business logic.
        *   **Function:**
            *   Must return a single value.
            *   Typically used in SQL expressions (e.g., `SELECT` clause, `WHERE` clause).
            *   Generally should not perform DML operations (though some database systems allow it, it's not best practice for functions used in SQL queries).
            *   Primarily used for calculations or returning a specific value.

*   Q44 - What are triggers and what are their types?
    *   **A44:**
        *   **Trigger:** A special type of stored procedure that automatically executes or "fires" when a specific event occurs in the database. These events can be DML operations (`INSERT`, `UPDATE`, `DELETE`) on a table, or DDL operations (`CREATE`, `ALTER`, `DROP`).
        *   **Types of Triggers (based on timing and level):**
            *   **Timing:**
                *   **`BEFORE` Trigger:** Fires before the triggering event occurs. Useful for data validation or auditing before changes are made.
                *   **`AFTER` Trigger:** Fires after the triggering event occurs. Useful for logging changes or performing actions based on the completed operation.
            *   **Level:**
                *   **`ROW-LEVEL` Trigger (`FOR EACH ROW`):** Fires once for each row affected by the DML statement.
                *   **`STATEMENT-LEVEL` Trigger (`FOR EACH STATEMENT`):** Fires once for the entire DML statement, regardless of how many rows are affected).

#### Indexing

*   Q45 - Define an index and its types?
    *   **A45:**
        *   **Index:** A database index is a data structure that improves the speed of data retrieval operations on a database table at the cost of additional writes and storage space to maintain the index data structure. It's similar to an index in a book, allowing the database system to quickly locate specific rows without scanning the entire table.
        *   **Types of Indexes:**
            *   **Clustered Index:** Determines the physical order of data in a table. A table can have only one clustered index. The data rows themselves are stored in the order of the clustered index key.
            *   **Non-Clustered Index:** Does not alter the physical order of the table rows. Instead, it creates a separate structure that contains the indexed columns and pointers to the actual data rows. A table can have multiple non-clustered indexes.
            *   **Unique Index:** Ensures that all values in the indexed column(s) are unique.
            *   **Composite/Compound Index:** An index on multiple columns.
            *   **Full-Text Index:** Used for efficient searching of text data within columns.

*   Q46 - What is the difference between clustered and non-clustered indexes?
    *   **A46:**
        *   **Clustered Index:**
            *   Defines the physical storage order of the data rows in the table.
            *   There can be only one clustered index per table.
            *   The leaf level of a clustered index *is* the data pages of the table.
            *   Generally faster for retrieving data when the data is accessed sequentially or within a range.
        *   **Non-Clustered Index:**
            *   Does not affect the physical storage order of the data rows.
            *   Can have multiple non-clustered indexes per table.
            *   The leaf level of a non-clustered index contains pointers to the actual data rows (or the clustered index key if one exists).
            *   Generally faster for retrieving data when the data is accessed randomly or when covering queries (where all requested columns are in the index).

#### Subqueries

*   Q47 - Define a subquery and its types?
    *   **A47:**
        *   **Subquery (or Inner Query/Nested Query):** A query nested inside another SQL query. It executes first, and its result is then used by the outer query. Subqueries can be used in various SQL clauses like `SELECT`, `FROM`, `WHERE`, and `HAVING`.
        *   **Types of Subqueries:**
            *   **Single-Row Subquery:** Returns zero or one row. Used with single-row comparison operators (`=`, `>`, `<`, `>=`, `<=`, `<>`).
            *   **Multi-Row Subquery:** Returns one or more rows. Used with multi-row comparison operators (`IN`, `NOT IN`, `ANY`, `ALL`, `EXISTS`, `NOT EXISTS`).
            *   **Multi-Column Subquery:** Returns one or more columns.
            *   **Correlated Subquery:** A subquery that depends on the outer query for its values. It executes once for each row processed by the outer query.
            *   **Non-Correlated Subquery (or Independent Subquery):** A subquery that can be executed independently of the outer query. Its result is passed to the outer query.

#### Miscellaneous SQL

*   Q48 - Provide examples of common SQL statements for DDL, DML, and DCL operations.
    *   **A48:**
        *   **DDL (Data Definition Language) Examples:**
            *   `CREATE TABLE Employees (ID INT PRIMARY KEY, Name VARCHAR(50));`
            *   `ALTER TABLE Employees ADD COLUMN Email VARCHAR(100);`
            *   `DROP TABLE Employees;`
        *   **DML (Data Manipulation Language) Examples:**
            *   `INSERT INTO Employees (ID, Name) VALUES (1, 'Alice');`
            *   `SELECT * FROM Employees WHERE Name = 'Alice';`
            *   `UPDATE Employees SET Email = 'alice@example.com' WHERE ID = 1;`
            *   `DELETE FROM Employees WHERE ID = 1;`
        *   **DCL (Data Control Language) Examples:**
            *   `GRANT SELECT ON Employees TO user1;`
            *   `REVOKE SELECT ON Employees FROM user1;`

*   Q49 - What is SQL (Structured Query Language)?
    *   **A49:** SQL (Structured Query Language) is a standard language for managing and manipulating relational databases. It is used to communicate with a database, allowing users to perform tasks such as creating and modifying database schemas, inserting, retrieving, updating, and deleting data.

*   Q50 - After creating a database table, can you add an additional column?
    *   **A50:** Yes, you can add an additional column to an existing database table using the `ALTER TABLE` statement with the `ADD COLUMN` clause.
        **Example:**
        ```sql
        ALTER TABLE Customers
        ADD COLUMN PhoneNumber VARCHAR(20);
        ```

*   Q51 - What is SQL Injection and how can it be prevented?
    *   **A51:**
        *   **SQL Injection:** A code injection technique used to attack data-driven applications, in which malicious SQL statements are inserted into an entry field for execution (e.g., to dump database contents to the attacker). It occurs when an application uses user-supplied input directly in SQL queries without proper validation or sanitization.
        *   **Prevention:**
            *   **Parameterized Queries (Prepared Statements):** The most effective way. This separates the SQL code from the user-supplied data, preventing the data from being interpreted as executable SQL.
            *   **Input Validation:** Validate and sanitize all user input to ensure it conforms to expected formats and does not contain malicious characters.
            *   **Least Privilege:** Grant database users only the necessary permissions.
            *   **Escaping User Input:** While less secure than parameterized queries, escaping special characters in user input can help prevent some injection attacks.

*   Q52 - What is NVL (or ISNULL/COALESCE) in SQL?
    *   **A52:** `NVL`, `ISNULL`, and `COALESCE` are functions used to handle `NULL` values in SQL queries, returning an alternative value if an expression is `NULL`.
        *   **`NVL(expression, replacement)`:** (Oracle specific) Returns `replacement` if `expression` is `NULL`, otherwise returns `expression`.
        *   **`ISNULL(expression, replacement)`:** (SQL Server specific) Returns `replacement` if `expression` is `NULL`, otherwise returns `expression`.
        *   **`COALESCE(expression1, expression2, ..., expressionN)`:** (Standard SQL) Returns the first non-`NULL` expression in the list. It's more flexible as it can take multiple arguments.

*   Q53 - How can you identify and extract duplicate data in SQL?
    *   **A53:**
        *   **Identifying Duplicates:** You can identify duplicate rows using the `GROUP BY` clause with the `COUNT()` aggregate function and the `HAVING` clause.
            **Example:**
            ```sql
            SELECT column1, column2, COUNT(*)
            FROM YourTable
            GROUP BY column1, column2
            HAVING COUNT(*) > 1;
            ```
        *   **Extracting Duplicates (keeping one unique record):** You can use `ROW_NUMBER()` or `CTE`s to assign a unique number to each row within a partition and then select only the first one.
            **Example (using `ROW_NUMBER()`):**
            ```sql
            WITH CTE_Duplicates AS (
                SELECT
                    *,
                    ROW_NUMBER() OVER (PARTITION BY column1, column2 ORDER BY (SELECT NULL)) as rn
                FROM YourTable
            )
            SELECT *
            FROM CTE_Duplicates
            WHERE rn = 1; -- To keep one unique record
            -- WHERE rn > 1; -- To get only the duplicate records
            ```

*   Q54 - What is the ALTER statement in SQL?
    *   **A54:** The `ALTER` statement in SQL is a DDL (Data Definition Language) command used to modify the structure of an existing database object, such as a table. It allows you to add, modify, or drop columns, add or drop constraints, and perform other structural changes without recreating the entire table.
        **Common uses:**
        *   `ALTER TABLE table_name ADD COLUMN column_name datatype;` (Add a column)
        *   `ALTER TABLE table_name DROP COLUMN column_name;` (Drop a column)
        *   `ALTER TABLE table_name ALTER COLUMN column_name datatype;` (Modify column datatype - syntax varies by DB)
        *   `ALTER TABLE table_name ADD CONSTRAINT constraint_name PRIMARY KEY (column_name);` (Add a constraint)

#### Relationships

*   Q55 - What are the different types of relationships in a database (e.g., one-to-one, one-to-many, many-to-many)?
    *   **A55:** Relationships in a database define how tables are connected to each other. The main types are:
        *   **One-to-One (1:1):** Each record in Table A can have at most one matching record in Table B, and vice versa. This is often used to split a table for security reasons, or to store rarely accessed data in a separate table.
            *   *Example:* A `Person` table and a `PassportDetails` table, where each person has one passport and each passport belongs to one person.
        *   **One-to-Many (1:M):** Each record in Table A can have many matching records in Table B, but each record in Table B can have only one matching record in Table A. This is the most common type of relationship.
            *   *Example:* A `Department` table and an `Employee` table, where one department can have many employees, but each employee belongs to only one department.
        *   **Many-to-Many (M:N):** Each record in Table A can have many matching records in Table B, and each record in Table B can have many matching records in Table A. This type of relationship requires a third table, called a "junction" or "associative" table, to resolve the relationship.
            *   *Example:* A `Student` table and a `Course` table, where one student can enroll in many courses, and one course can have many students.

*   Q56 - How do you implement a many-to-many relationship between two tables?
    *   **A56:** A many-to-many relationship is implemented using a third table, often called a **junction table**, **associative table**, or **bridge table**. This junction table contains foreign keys that reference the primary keys of the two tables involved in the many-to-many relationship.
        *   **Steps:**
            1.  Create the two main tables (e.g., `Students` and `Courses`).
            2.  Create a new junction table (e.g., `StudentCourses`).
            3.  In the junction table, add two columns that will serve as foreign keys, referencing the primary keys of the `Students` and `Courses` tables.
            4.  The combination of these two foreign keys in the junction table typically forms a composite primary key for the junction table, ensuring uniqueness for each student-course enrollment.

        *Example (SQL):*
        ```sql
        CREATE TABLE Students (
            StudentID INT PRIMARY KEY,
            StudentName VARCHAR(100)
        );

        CREATE TABLE Courses (
            CourseID INT PRIMARY KEY,
            CourseName VARCHAR(100)
        );

        CREATE TABLE StudentCourses (
            StudentID INT,
            CourseID INT,
            EnrollmentDate DATE,
            PRIMARY KEY (StudentID, CourseID),
            FOREIGN KEY (StudentID) REFERENCES Students(StudentID),
            FOREIGN KEY (CourseID) REFERENCES Courses(CourseID)
        );
        ```

*   Q57 - How do you map a one-to-one relationship?
    *   **A57:** A one-to-one relationship can be mapped in a few ways:
        1.  **Combine into a single table:** If the two entities are very closely related and always accessed together, you can put all attributes into a single table. This is often done if one entity is just an extension of the other.
        2.  **Separate tables with a shared primary key:** Create two separate tables, where the primary key of one table also serves as the primary key (and foreign key) in the second table. This is useful when you want to logically separate data, or if some attributes are optional and rarely accessed.
            *Example (SQL):*
            ```sql
            CREATE TABLE Persons (
                PersonID INT PRIMARY KEY,
                FirstName VARCHAR(50),
                LastName VARCHAR(50)
            );

            CREATE TABLE PassportDetails (
                PersonID INT PRIMARY KEY, -- Also acts as FOREIGN KEY
                PassportNumber VARCHAR(20) UNIQUE,
                IssueDate DATE,
                ExpiryDate DATE,
                FOREIGN KEY (PersonID) REFERENCES Persons(PersonID)
            );
            ```
        3.  **Separate tables with a unique foreign key:** Create two separate tables, and place a foreign key in one table that references the primary key of the other table, and ensure this foreign key also has a `UNIQUE` constraint. This is less common than the shared primary key approach for strict 1:1 relationships but can be used.

#### Data Warehousing and Business Intelligence

*   Q58 - Explain Star Schema and Snowflake Schema in data warehousing.
    *   **A58:** These are two common types of dimensional modeling schemas used in data warehouses.
        *   **Star Schema:**
            *   Consists of a central **fact table** and multiple **dimension tables** directly connected to it.
            *   Dimension tables are not normalized (denormalized), meaning they might contain redundant data.
            *   Simpler design, easier to understand and navigate.
            *   Fewer joins required for queries, leading to faster query performance.
            *   Less flexible for complex hierarchies.
        *   **Snowflake Schema:**
            *   Similar to a star schema, but the dimension tables are normalized into multiple related tables.
            *   Dimension tables are further broken down into sub-dimension tables.
            *   More complex design, requires more joins for queries, potentially slower performance.
            *   Reduces data redundancy and improves data integrity.
            *   More flexible for complex hierarchies and attribute relationships.

*   Q59 - What is a hypothesis?
    *   **A59:** In statistics, a hypothesis is a testable statement or a proposed explanation for a phenomenon. It's an educated guess or a tentative assumption made about a population parameter or a relationship between variables, which can then be tested through observation or experimentation.

*   Q60 - When should you use mean versus median?
    *   **A60:**
        *   **Mean (Average):**
            *   **Use when:** The data is symmetrically distributed (e.g., normal distribution) and does not contain significant outliers. It uses all data points in its calculation.
            *   **Sensitive to:** Outliers, as extreme values can heavily influence the mean.
        *   **Median (Middle Value):**
            *   **Use when:** The data is skewed or contains outliers. The median is less affected by extreme values.
            *   **Robust to:** Outliers.

*   Q61 - What are sampling techniques?
    *   **A61:** Sampling techniques are methods used to select a subset of individuals or observations from a larger population. The goal is to make inferences about the entire population based on the characteristics of the sample, without having to collect data from every single member of the population.

*   Q62 - What are the types of sampling?
    *   **A62:** Sampling techniques are broadly categorized into two main types:
        *   **Probability Sampling (Random Sampling):** Each member of the population has a known, non-zero chance of being selected. This allows for statistical inference and generalization to the population.
            *   **Simple Random Sampling:** Every member has an equal chance of selection.
            *   **Systematic Sampling:** Selecting every nth member from a list.
            *   **Stratified Sampling:** Dividing the population into homogeneous subgroups (strata) and then randomly sampling from each stratum.
            *   **Cluster Sampling:** Dividing the population into clusters and then randomly selecting entire clusters to sample.
        *   **Non-Probability Sampling (Non-Random Sampling):** Selection is based on the researcher's subjective judgment or convenience, not random chance. This makes it difficult to generalize findings to the entire population.
            *   **Convenience Sampling:** Selecting participants who are easily accessible.
            *   **Quota Sampling:** Selecting participants based on specific characteristics to match population proportions.
            *   **Purposive/Judgmental Sampling:** Selecting participants based on the researcher's expertise and judgment.
            *   **Snowball Sampling:** Participants recruit other participants from their network.

*   Q63 - What is an operational data store (ODS)?
    *   **A63:** An Operational Data Store (ODS) is a database designed to integrate data from multiple operational systems (e.g., CRM, ERP) for operational reporting and analysis. It typically contains current or near-current data, often updated in real-time or near real-time, and serves as an interim area for data before it's loaded into a data warehouse. It's used for immediate operational decision-making.

*   Q64 - Explain the 'non-volatile' characteristic of a data warehouse.
    *   **A64:** The 'non-volatile' characteristic of a data warehouse means that once data is loaded into the data warehouse, it is not updated or deleted. New data is added incrementally, but existing data remains unchanged. This ensures that historical data is preserved for analysis and reporting, providing a consistent view of business trends over time. It contrasts with operational systems where data is constantly updated and deleted.

*   Q65 - What is hypothesis testing and what are its types?
    *   **A65:**
        *   **Hypothesis Testing:** A statistical method used to make decisions about a population based on sample data. It involves formulating a null hypothesis (H0) and an alternative hypothesis (H1), collecting data, and then using statistical tests to determine whether there is enough evidence to reject the null hypothesis.
        *   **Types of Hypothesis Tests (broadly):**
            *   **Parametric Tests:** Assume the data follows a specific distribution (e.g., normal distribution) and make assumptions about population parameters. Examples: t-test, ANOVA, Z-test.
            *   **Non-Parametric Tests:** Do not assume a specific distribution for the data and are used when parametric assumptions are violated or with ordinal/nominal data. Examples: Chi-squared test, Mann-Whitney U test, Wilcoxon signed-rank test.

*   Q66 - What is a p-value?
    *   **A66:** In hypothesis testing, the p-value (probability value) is the probability of obtaining test results at least as extreme as the observed results, assuming that the null hypothesis is true.
        *   **Interpretation:**
            *   A small p-value (typically ≤ 0.05) indicates strong evidence against the null hypothesis, leading to its rejection.
            *   A large p-value (> 0.05) indicates weak evidence against the null hypothesis, meaning you fail to reject it.

*   Q67 - How do you find outliers in data?
    *   **A67:** Outliers are data points that significantly differ from other observations. Methods to find outliers include:
        *   **Statistical Methods:**
            *   **Z-score:** Measures how many standard deviations away a data point is from the mean. A common threshold is a Z-score greater than 2 or 3.
            *   **IQR (Interquartile Range):** Data points outside 1.5 * IQR below Q1 (first quartile) or above Q3 (third quartile) are considered outliers.
            *   **Box Plots:** Visual representation where outliers are plotted as individual points beyond the "whiskers".
        *   **Machine Learning Methods:**
            *   **Isolation Forest:** An algorithm that isolates anomalies.
            *   **One-Class SVM:** A support vector machine used for anomaly detection.
            *   **DBSCAN:** A clustering algorithm that can identify noise points as outliers.
        *   **Visual Inspection:** Scatter plots, histograms, and box plots can help visually identify outliers.

*   Q68 - What is conditional probability?
    *   **A68:** Conditional probability is the probability of an event occurring given that another event has already occurred. It is denoted as P(A|B), which means the probability of event A happening given that event B has already happened.
        **Formula:** P(A|B) = P(A and B) / P(B)

*   Q69 - Why is a data warehouse used?
    *   **A69:** A data warehouse is used for:
        *   **Business Intelligence (BI) and Analytics:** Provides a centralized repository of integrated, historical data for reporting, analysis, and decision-making.
        *   **Historical Data Analysis:** Stores historical data over long periods, enabling trend analysis, forecasting, and comparison.
        *   **Improved Query Performance:** Optimized for complex analytical queries, unlike operational databases.
        *   **Data Consistency and Quality:** Integrates data from disparate sources, cleanses it, and ensures consistency.
        *   **Strategic Decision Making:** Supports strategic planning by providing a comprehensive view of business performance.

*   Q70 - What are the types of dimensions in a data warehouse?
    *   **A70:** Dimensions in a data warehouse provide the context for the facts (measures) in the fact table. Common types include:
        *   **Conformed Dimension:** A dimension that is shared across multiple fact tables, ensuring consistent reporting across different business processes.
        *   **Junk Dimension:** A dimension table that combines several low-cardinality flags and attributes into a single dimension to avoid creating many small dimension tables.
        *   **Role-Playing Dimension:** A single physical dimension table that is used multiple times in a fact table, with each usage representing a different role. (e.g., a Date dimension used for Order Date, Ship Date, Delivery Date).
        *   **Degenerate Dimension:** A dimension key that is stored directly within the fact table and does not have its own dimension table. It's typically an operational transaction number.
        *   **Slowly Changing Dimension (SCD):** Dimensions whose attributes change over time. Different types of SCDs (Type 1, Type 2, Type 3) handle these changes differently.

*   Q71 - What are the major components of a data warehouse?
    *   **A71:** The major components of a data warehouse typically include:
        *   **Data Sources:** Operational systems, external data, etc.
        *   **Data Staging Area (ETL/ELT):** Where data is extracted, transformed, and loaded.
        *   **Data Warehouse Database:** The central repository for integrated, historical data.
        *   **Data Marts:** Subset of the data warehouse, designed for specific business functions or departments.
        *   **Metadata Repository:** Stores information about the data warehouse (data definitions, source mappings, etc.).
        *   **Access Tools:** Tools for reporting, querying, analysis, and data mining (BI tools).

*   Q72 - What is a data mart?
    *   **A72:** A data mart is a subset of a data warehouse that is designed to serve the needs of a specific business function, department, or group of users. It focuses on a particular subject area (e.g., sales, marketing, finance) and contains a more limited scope of data compared to the enterprise-wide data warehouse.

*   Q73 - What is the difference between Star Schema and Snowflake Schema?
    *   **A73:** (Answered in Q58, but can reiterate key differences)
        *   **Star Schema:** Simpler, denormalized dimensions, fewer joins, faster queries.
        *   **Snowflake Schema:** More complex, normalized dimensions, more joins, potentially slower queries, less data redundancy.

*   Q74 - What are the types of schemas in a data warehouse?
    *   **A74:** The primary types of schemas in data warehousing are:
        *   **Star Schema:** (See Q58)
        *   **Snowflake Schema:** (See Q58)
        *   **Fact Constellation Schema (Galaxy Schema):** Consists of multiple fact tables sharing some dimension tables. It's used for more complex data warehouse designs involving multiple business processes.

*   Q75 - Which schema is more denormalized: Snowflake or Star Schema, and which is faster for data retrieval?
    *   **A75:**
        *   **More Denormalized:** Star Schema is more denormalized because its dimension tables are not normalized and contain all attributes directly.
        *   **Faster for Data Retrieval:** Star Schema is generally faster for data retrieval because it requires fewer joins to retrieve data, as dimensions are directly linked to the fact table. Snowflake schema requires more joins due to its normalized dimensions, which can impact query performance.

*   Q76 - What is the difference between Big Data and a Data Warehouse?
    *   **A76:**
        *   **Big Data:** Refers to extremely large and complex datasets that cannot be processed or analyzed using traditional data processing applications. It's characterized by the "3 Vs": Volume, Velocity, and Variety. Big Data often includes unstructured and semi-structured data.
        *   **Data Warehouse:** A system designed for reporting and data analysis, and is a central repository of integrated data from one or more disparate sources. Data in a data warehouse is typically structured, cleaned, and transformed for analytical purposes.

#### Statistics

*   Q77 - What is descriptive statistics?
    *   **A77:** Descriptive statistics are used to summarize and describe the main features of a collection of information (data). They provide simple summaries about the sample and the measures. Descriptive statistics are typically distinguished from inferential statistics, which are used to make predictions or inferences about a population based on a sample of data. Common descriptive statistics include measures of central tendency (mean, median, mode) and measures of variability (range, variance, standard deviation).

*   Q78 - When should you use the median instead of the mean?
    *   **A78:** You should use the median instead of the mean when the data is skewed (not symmetrically distributed) or contains significant outliers. The median is a more robust measure of central tendency in such cases because it is less affected by extreme values, providing a more representative "typical" value for the dataset.

*   Q79 - Define mean, variance, and standard deviation, and explain when to use each.
    *   **A79:**
        *   **Mean (Average):**
            *   **Definition:** The sum of all values divided by the number of values.
            *   **When to use:** Best for symmetrically distributed data without extreme outliers. It uses all data points and is good for general summaries.
        *   **Variance:**
            *   **Definition:** A measure of how spread out the data is from the mean. It's the average of the squared differences from the mean.
            *   **When to use:** Used to quantify the dispersion of a set of data points. A higher variance indicates that data points are spread out over a wider range of values. It's often used in statistical tests (e.g., ANOVA) and as an intermediate step to calculate standard deviation.
        *   **Standard Deviation:**
            *   **Definition:** The square root of the variance. It measures the average amount of variability or dispersion around the mean, expressed in the same units as the data.
            *   **When to use:** Most commonly used measure of spread. It's easier to interpret than variance because it's in the original units of the data. Useful for understanding the typical distance of data points from the mean and for comparing the spread of different datasets.

*   Q80 - How do you handle outliers in data?
    *   **A80:** Handling outliers depends on their cause and impact. Common approaches include:
        *   **Removal:** If outliers are due to data entry errors or measurement errors, they can be removed. However, this should be done cautiously as it can lead to loss of information.
        *   **Transformation:** Apply mathematical transformations (e.g., logarithmic, square root) to the data to reduce the impact of extreme values.
        *   **Imputation:** Replace outliers with a more representative value, such as the mean, median, or a value derived from a statistical model.
        *   **Binning:** Group data into bins, which can smooth out the effect of outliers.
        *   **Separate Analysis:** Analyze outliers separately if they represent a distinct and important phenomenon.
        *   **Robust Statistical Methods:** Use statistical methods that are less sensitive to outliers (e.g., median instead of mean, robust regression).

#### Other

*   Q81 - What are the advantages and disadvantages of databases?
    *   **A81:**
        *   **Advantages:**
            *   **Data Redundancy Control:** Minimizes duplicate data, saving storage and preventing inconsistencies.
            *   **Data Consistency:** Ensures data is accurate and reliable across the system.
            *   **Data Sharing:** Allows multiple users and applications to access and share data concurrently.
            *   **Data Integrity:** Enforces rules and constraints to maintain data quality.
            *   **Data Security:** Provides mechanisms for access control and data protection.
            *   **Data Independence:** Separates the data from the applications, allowing changes to one without affecting the other.
            *   **Backup and Recovery:** Offers tools for backing up and restoring data in case of failures.
        *   **Disadvantages:**
            *   **Complexity:** Designing, implementing, and managing a database system can be complex.
            *   **Cost:** High initial investment in hardware, software, and personnel.
            *   **Performance Overhead:** Can have performance overhead due to the layers of abstraction and general-purpose nature.
            *   **Security Risks:** If not properly secured, databases can be vulnerable to attacks.
            *   **Vendor Lock-in:** Dependence on a specific database vendor can make migration difficult.

*   Q82 - Provide examples of different database systems (e.g., Oracle, Microsoft SQL Server, DB2, MySQL).
    *   **A82:**
        *   **Relational Database Management Systems (RDBMS):**
            *   **Oracle Database:** A powerful, widely used commercial RDBMS, known for its robustness, scalability, and advanced features.
            *   **Microsoft SQL Server:** A popular RDBMS from Microsoft, commonly used in enterprise environments, especially with Windows-based applications.
            *   **IBM Db2:** A family of relational database products from IBM, often used in large enterprise and mainframe environments.
            *   **MySQL:** A popular open-source RDBMS, widely used for web applications and smaller to medium-sized projects.
            *   **PostgreSQL:** A powerful, open-source object-relational database system known for its strong adherence to SQL standards and advanced features.
            *   **SQLite:** A small, self-contained, serverless, zero-configuration, transactional SQL database engine, often embedded in applications.
        *   **NoSQL Databases:**
            *   **MongoDB:** A document-oriented NoSQL database, storing data in flexible, JSON-like documents.
            *   **Cassandra:** A distributed NoSQL database designed to handle large amounts of data across many commodity servers, providing high availability.
            *   **Redis:** An open-source, in-memory data structure store, used as a database, cache, and message broker.
            *   **Neo4j:** A graph database, optimized for storing and querying highly connected data.

*   Q83 - What is a class?
    *   **A83:** In object-oriented programming (OOP), a class is a blueprint or a template for creating objects. It defines a set of attributes (data/properties) and methods (functions/behaviors) that all objects of that class will possess. A class itself is not an object; it's a logical construct that describes what an object will look like and how it will behave. Objects are instances of classes.

*   Q84 - What are common data types in SQL?
    *   **A84:** Common data types in SQL include:
        *   **Numeric Types:**
            *   `INT` (INTEGER): Whole numbers.
            *   `DECIMAL(p, s)` or `NUMERIC(p, s)`: Exact numeric values with a specified precision (p) and scale (s).
            *   `FLOAT` or `REAL`: Floating-point numbers (approximate numeric values).
            *   `DOUBLE PRECISION`: Double-precision floating-point numbers.
        *   **String Types:**
            *   `VARCHAR(n)`: Variable-length string with a maximum length of n.
            *   `CHAR(n)`: Fixed-length string with a length of n.
            *   `TEXT`: Variable-length string for large amounts of text.
        *   **Date and Time Types:**
            *   `DATE`: Stores a date (year, month, day).
            *   `TIME`: Stores a time (hour, minute, second).
            *   `DATETIME` or `TIMESTAMP`: Stores both date and time.
        *   **Boolean Type:**
            *   `BOOLEAN` or `BOOL`: Stores true/false values (some databases use `TINYINT(1)` or similar).

*   Q85 - What are common data types in programming (e.g., Python)?
    *   **A85:** Common data types in programming languages like Python include:
        *   **Numeric Types:**
            *   `int`: Integers (whole numbers).
            *   `float`: Floating-point numbers (numbers with decimal points).
            *   `complex`: Complex numbers (e.g., `3 + 2j`).
        *   **Sequence Types:**
            *   `str`: Strings (sequences of characters).
            *   `list`: Ordered, mutable sequences of items.
            *   `tuple`: Ordered, immutable sequences of items.
        *   **Mapping Type:**
            *   `dict`: Dictionaries (unordered collections of key-value pairs).
        *   **Set Types:**
            *   `set`: Unordered collections of unique items.
            *   `frozenset`: Immutable version of a set.
        *   **Boolean Type:**
            *   `bool`: Boolean values (`True` or `False`).
        *   **None Type:**
            *   `NoneType`: Represents the absence of a value (`None`).

*   Q86 - What are the ACID properties in database transactions?
    *   **A86:** ACID is an acronym that defines a set of properties that guarantee that database transactions are processed reliably.
        *   **Atomicity:** A transaction is treated as a single, indivisible unit of work. Either all of its operations are completed successfully, or none of them are. If any part of the transaction fails, the entire transaction is rolled back, leaving the database in its state before the transaction began.
        *   **Consistency:** A transaction brings the database from one valid state to another valid state. It ensures that all data validation rules, constraints, and triggers are maintained. If a transaction violates any of these rules, it is rolled back.
        *   **Isolation:** Concurrent transactions are executed in such a way that they appear to be executed sequentially. Each transaction is unaware of other transactions executing concurrently, preventing interference and ensuring that the intermediate state of one transaction is not visible to others.
        *   **Durability:** Once a transaction has been committed, its changes are permanent and will survive system failures (e.g., power outages, crashes). The committed data is written to non-volatile storage.

*   Q87 - Explain SQL window functions and provide an example.
    *   **A87:**
        *   **SQL Window Functions:** Perform a calculation across a set of table rows that are related to the current row. Unlike aggregate functions (which return a single value for a group), window functions return a value for each row in the result set. They operate on a "window" of rows defined by the `OVER()` clause.
        *   **Common Uses:** Calculating running totals, moving averages, ranking, or comparing a row's value to a preceding or following row.
        *   **Example (Calculating a running total):**
            ```sql
            SELECT
                OrderDate,
                SalesAmount,
                SUM(SalesAmount) OVER (ORDER BY OrderDate) as RunningTotal
            FROM Sales
            ORDER BY OrderDate;
            ```
            In this example, `SUM(SalesAmount) OVER (ORDER BY OrderDate)` calculates the running total of `SalesAmount` for each `OrderDate`.

*   Q88 - What is a Common Table Expression (CTE) in SQL and when would you use it?
    *   **A88:**
        *   **Common Table Expression (CTE):** A temporary, named result set that you can reference within a single SQL statement (e.g., `SELECT`, `INSERT`, `UPDATE`, `DELETE`). It's defined using the `WITH` clause. CTEs are not stored as objects in the database and only exist for the duration of the query.
        *   **When to use it:**
            *   **Readability:** To break down complex, multi-step queries into logical, readable blocks.
            *   **Recursion:** To perform recursive queries (e.g., hierarchical data).
            *   **Reusability:** To reference the same subquery multiple times within a larger query without rewriting it.
            *   **Simplifying Joins and Subqueries:** Can make complex joins and nested subqueries easier to manage.

*   Q89 - Explain the core data structures in Pandas (Series and DataFrame) and their uses.
    *   **A89:** Pandas is a popular Python library for data manipulation and analysis. Its two core data structures are:
        *   **Series:**
            *   **Definition:** A one-dimensional labeled array capable of holding any data type (integers, strings, floats, Python objects, etc.). It's similar to a column in a spreadsheet or a SQL table, or a dictionary in Python.
            *   **Uses:** Representing a single column of data, time series data, or any one-dimensional data with labels.
        *   **DataFrame:**
            *   **Definition:** A two-dimensional labeled data structure with columns of potentially different types. It's similar to a spreadsheet, a SQL table, or a dictionary of Series objects.
            *   **Uses:** The primary data structure for most data analysis tasks in Pandas. Used for storing and manipulating tabular data, performing operations like filtering, sorting, grouping, merging, and reshaping data.

*   Q90 - Briefly explain the concept of supervised vs. unsupervised learning.
    *   **A90:** These are two fundamental categories of machine learning:
        *   **Supervised Learning:**
            *   **Concept:** The model learns from a labeled dataset, meaning the input data has corresponding "correct" output labels. The goal is to learn a mapping from inputs to outputs so that the model can predict outputs for new, unseen data.
            *   **Tasks:** Regression (predicting continuous values, e.g., house prices) and Classification (predicting discrete categories, e.g., spam detection).
            *   **Examples:** Linear Regression, Logistic Regression, Support Vector Machines, Decision Trees.
        *   **Unsupervised Learning:**
            *   **Concept:** The model learns from an unlabeled dataset, meaning there are no "correct" output labels provided. The goal is to find hidden patterns, structures, or relationships within the data.
            *   **Tasks:** Clustering (grouping similar data points), Dimensionality Reduction (reducing the number of features), Association Rule Mining.
            *   **Examples:** K-Means Clustering, Principal Component Analysis (PCA), Apriori algorithm.

*   Q91 - Explain the Central Limit Theorem and its significance.
    *   **A91:**
        *   **Central Limit Theorem (CLT):** States that, given a sufficiently large sample size from a population with a finite level of variance, the sampling distribution of the mean of these samples will be approximately normally distributed, regardless of the population's actual distribution. The larger the sample size, the more closely the sampling distribution will resemble a normal distribution.
        *   **Significance:**
            *   **Foundation for Inferential Statistics:** It allows us to use normal distribution-based statistical methods (like Z-tests, t-tests) to make inferences about population parameters, even if the population distribution is not normal, as long as the sample size is large enough.
            *   **Simplifies Statistical Analysis:** Without the CLT, statistical analysis would be much more complex, as we would need to know the exact distribution of the population to make accurate inferences.
            *   **Underpins Many Statistical Tests:** Many common statistical tests and confidence intervals rely on the assumption of normality of the sampling distribution, which the CLT helps to justify.

*   Q92 - Explain the difference between Type I and Type II errors in hypothesis testing.
    *   **A92:** In hypothesis testing, there are two types of errors that can occur:
        *   **Type I Error (False Positive):**
            *   **Definition:** Rejecting a true null hypothesis.
            *   **Symbol:** Denoted by α (alpha), also known as the significance level.
            *   **Analogy:** Convicting an innocent person.
            *   **Risk:** The probability of making a Type I error is set by the researcher (e.g., α = 0.05 means a 5% chance of a Type I error).
        *   **Type II Error (False Negative):**
            *   **Definition:** Failing to reject a false null hypothesis.
            *   **Symbol:** Denoted by β (beta).
            *   **Analogy:** Letting a guilty person go free.
            *   **Risk:** The probability of making a Type II error is inversely related to the power of the test (1 - β).


## Object Oriented

*   Q93 - What is Object-Oriented Programming (OOP)?
    *   **A93:** Object-Oriented Programming (OOP) is a programming paradigm based on the concept of "objects", which can contain data in the form of fields (often known as attributes or properties) and code in the form of procedures (often known as methods). A key feature of OOP is that an object's own procedures can access and often modify its own data fields.

*   Q94 - What are the basic concepts of OOP?
    *   **A94:** The fundamental concepts of OOP are:
        *   **Abstraction:** Hiding the complex implementation details and showing only the essential features of the object.
        *   **Encapsulation:** Binding together the data and the methods that manipulate the data, and keeping both safe from outside interference and misuse.
        *   **Inheritance:** The mechanism by which one class can inherit the properties and methods of another class, promoting code reuse.
        *   **Polymorphism:** The ability of an object to take on many forms. The most common use of polymorphism in OOP occurs when a parent class reference is used to refer to a child class object.

*   Q95 - What is the difference between a class and an object?
    *   **A95:**
        *   **Class:** A blueprint or template for creating objects. It defines a set of properties and methods that are common to all objects of one type.
        *   **Object:** An instance of a class. It is a concrete entity that has its own state (values for its properties) and behavior (its methods).

*   Q96 - What is the difference between method overloading and method overriding?
    *   **A96:**
        *   **Method Overloading:** Occurs when two or more methods in the same class have the same name but different parameters (different number of arguments, or different types of arguments, or both). This is a way to achieve compile-time (static) polymorphism.
        *   **Method Overriding:** Occurs when a subclass has a method with the same name, parameters, and return type as a method in its superclass. The method in the subclass is said to override the method in the superclass. This is a way to achieve run-time (dynamic) polymorphism.

*   Q97 - What is the difference between an abstract class and an interface?
    *   **A97:**
        *   **Abstract Class:** A class that cannot be instantiated and is meant to be inherited by other classes. It can have both abstract methods (methods without a body) and concrete methods (methods with a body). A class can inherit from only one abstract class.
        *   **Interface:** A completely abstract class that can only have abstract methods. A class can implement multiple interfaces. It is a way to achieve full abstraction and multiple inheritance in languages that don't support multiple inheritance of classes.

*   Q98 - What are constructors and destructors?
    *   **A98:**
        *   **Constructor:** A special method that is automatically called when an object of a class is created. It is used to initialize the object's state. A constructor has the same name as the class and no return type.
        *   **Destructor:** A special method that is automatically called when an object is destroyed. It is used to deallocate memory and do other cleanup for a class object and its class members when the object is destroyed. A destructor has the same name as the class but is preceded by a tilde (~).

*   Q99 - What are the different types of constructors?
    *   **A99:**
        *   **Default Constructor:** A constructor that takes no arguments.
        *   **Parameterized Constructor:** A constructor that takes one or more arguments.
        *   **Copy Constructor:** A constructor that creates an object by initializing it with an object of the same class, which has been created previously.

*   Q100 - What are access modifiers?
    *   **A100:** Access modifiers are keywords that set the accessibility or scope of a class, method, constructor, or variable. The most common access modifiers are:
        *   **Public:** The members are accessible from any other class.
        *   **Private:** The members are accessible only within the same class.
        *   **Protected:** The members are accessible within the same class, from subclasses, and from classes in the same package.

*   Q101 - What is the difference between static and dynamic binding?
    *   **A101:**
        *   **Static Binding (Early Binding):** The type of the object is determined at compile time. Method overloading is an example of static binding.
        *   **Dynamic Binding (Late Binding):** The type of the object is determined at run time. Method overriding is an example of dynamic binding.

*   Q102 - What is a virtual function?
    *   **A102:** A virtual function is a member function that you expect to be redefined in derived classes. When you refer to a derived class object using a pointer or a reference to the base class, you can call a virtual function for that object and execute the derived class's version of the function.

*   Q103 - What is a pure virtual function?
    *   **A103:** A pure virtual function is a virtual function for which we don’t have an implementation. We only declare it. A class containing a pure virtual function is an abstract class.

*   Q104 - What is a friend function?
    *   **A104:** A friend function of a class is defined outside that class' scope but it has the right to access all private and protected members of the class.

*   Q105 - What is the 'this' pointer?
    *   **A105:** The `this` pointer is a special pointer that holds the address of the current object. It is implicitly passed to all non-static member functions.

*   Q106 - What is exception handling?
    *   **A106:** Exception handling is a mechanism to handle runtime errors, such as ClassNotFoundException, IOException, SQLException, RemoteException, etc. The core advantage of exception handling is to maintain the normal flow of the application. The keywords `try`, `catch`, and `throw` are used for exception handling.

*   Q135 - What is an Inline function?
    *   **A135:** An inline function is a function that is expanded in line when it is called. That is, the compiler replaces the function call with the actual code of the function. This can improve performance by eliminating the overhead of a function call, but it can also increase code size if the function is large or called frequently.

*   Q136 - What is operator overloading?
    *   **A136:** Operator overloading is a feature that allows operators (like `+`, `-`, `*`, `/`, etc.) to be redefined or given special meaning for user-defined data types (classes). This allows operators to work with objects of a class in a way that is intuitive and consistent with their behavior on built-in types.

*   Q137 - What is a ternary operator?
    *   **A137:** The ternary operator (also known as the conditional operator) is a shorthand way to write an `if-else` statement. It takes three operands: a condition, an expression to execute if the condition is true, and an expression to execute if the condition is false.
        *   **Syntax:** `condition ? expression_if_true : expression_if_false;`

*   Q138 - What is the use of the finalize method?
    *   **A138:** The `finalize()` method (in languages like Java) is a special method that the garbage collector calls on an object just before that object is garbage collected. It is typically used to perform cleanup operations on resources that are not managed by the garbage collector, such as closing files or network connections. However, its use is generally discouraged due to unpredictable timing and performance issues.

*   Q139 - What are different types of arguments (Call by Value, Call by Reference)?
    *   **A139:**
        *   **Call by Value:** When arguments are passed by value, a copy of the actual argument's value is passed to the function. Any changes made to the parameter inside the function do not affect the original argument outside the function.
        *   **Call by Reference:** When arguments are passed by reference, a reference (or memory address) to the actual argument is passed to the function. This means that changes made to the parameter inside the function *do* affect the original argument outside the function.

*   Q140 - What is the super keyword?
    *   **A140:** The `super` keyword (in languages like Java) is used to refer to the immediate parent class object. It can be used to:
        *   Call the parent class's constructor.
        *   Access methods of the parent class that have been overridden by the child class.
        *   Access members (fields) of the parent class that are hidden by the child class.

*   Q141 - What are tokens?
    *   **A141:** In programming, a token is the smallest individual unit of a program that is meaningful to the compiler or interpreter. Tokens are typically categorized into keywords, identifiers, constants, string literals, operators, and punctuators.

*   Q142 - What is sealed modifiers?
    *   **A142:** A `sealed` modifier (in languages like C#) is used to prevent a class from being inherited by other classes. It can also be applied to methods or properties to prevent them from being overridden in derived classes.

*   Q143 - How can we call the base method without creating an instance?
    *   **A143:** You can call a base class method without creating an instance of the base class if the method is `static`. Static methods belong to the class itself, not to any specific instance of the class, and can be called directly using the class name (e.g., `BaseClass.staticMethod()`).

*   Q144 - What is the difference between new and override (in C# context)?
    *   **A144:**
        *   **`new` keyword:** Used to hide an inherited member from a base class. When a member in a derived class is declared with `new`, it creates a new member with the same name, effectively hiding the base class member. The base class member is still accessible if the object is cast to the base class type.
        *   **`override` keyword:** Used to extend or modify the implementation of an inherited virtual or abstract method, property, indexer, or event from a base class. When a member is `override`n, it replaces the base class's implementation, and the overridden method is called regardless of whether the object is cast to the base class or derived class type.

*   Q145 - What is the difference between a structure and a class?
    *   **A145:**
        *   **Structure (Struct):** Typically a value type (in languages like C# or C++). Often used for small, lightweight data structures that primarily hold data. Structs are usually allocated on the stack (though can be on the heap if part of a class). They generally do not support inheritance (though some languages allow interface implementation).
        *   **Class:** Typically a reference type. Used for more complex objects that encapsulate both data and behavior. Classes are allocated on the heap. They fully support inheritance and polymorphism.

*   Q146 - What are all the operators that cannot be overloaded?
    *   **A146:** The specific operators that cannot be overloaded vary slightly by language, but commonly include:
        *   Scope Resolution Operator (`::`)
        *   Member Selection Operator (`.`)
        *   Member Selection through Pointer to Member Operator (`.*`)
        *   Ternary Conditional Operator (`?:`)
        *   `sizeof` operator
        *   Typeid operator (`typeid`)

*   Q147 - Can a static method use non-static members?
    *   **A147:** No, a static method cannot directly use non-static (instance) members. Static methods belong to the class itself and are not associated with any specific object instance. Non-static members, on the other hand, belong to an object instance. To access a non-static member from a static method, you would need an instance of the class.

*   Q148 - What are base class, sub class, and super class?
    *   **A148:** These terms are used in the context of inheritance:
        *   **Base Class (or Parent Class / Super Class):** The class whose properties and methods are inherited by another class.
        *   **Sub Class (or Child Class / Derived Class):** The class that inherits properties and methods from another class (the base class).

## Data Science + Machine Learning + Data Mining (Data Science Track)

*   Q107 - What is data science?
    *   **A107:** Data science is an interdisciplinary field that uses scientific methods, processes, algorithms, and systems to extract knowledge and insights from noisy, structured, and unstructured data, and apply knowledge and actionable insights from data across a broad range of application domains.

*   Q108 - What is the difference between a data scientist and a data analyst?
    *   **A108:**
        *   **Data Analyst:** Focuses on analyzing existing data to answer specific questions, create reports, and visualize trends. They often work with structured data and use tools like SQL, Excel, and BI dashboards.
        *   **Data Scientist:** A broader role that involves collecting, cleaning, and processing data, building predictive models, and developing algorithms. They often work with both structured and unstructured data and use programming languages like Python and R, along with machine learning techniques.

*   Q109 - What is data cleaning? How do we clean the data?
    *   **A109:**
        *   **Data Cleaning (or Data Cleansing):** The process of detecting and correcting (or removing) corrupt or inaccurate records from a record set, table, or database and refers to identifying incomplete, incorrect, inaccurate or irrelevant parts of the data and then replacing, modifying, or deleting the dirty or coarse data.
        *   **How to clean data:**
            *   Handle missing values (imputation, deletion).
            *   Correct structural errors (typos, inconsistent formatting).
            *   Filter unwanted outliers (based on domain knowledge or statistical methods).
            *   Remove duplicate records.
            *   Standardize and normalize data.

*   Q110 - What is Data Mining?
    *   **A110:** Data mining is the process of discovering patterns, insights, and knowledge from large datasets. It involves techniques from machine learning, statistics, and database systems to extract valuable information for decision-making.

*   Q111 - What are the real-life applications of data mining and machine learning?
    *   **A111:**
        *   **Fraud Detection:** Identifying unusual patterns in transactions to detect fraudulent activities.
        *   **Recommendation Systems:** Suggesting products, movies, or content to users based on their past behavior and preferences (e.g., Netflix, Amazon).
        *   **Customer Segmentation:** Grouping customers based on their demographics and behavior for targeted marketing.
        *   **Medical Diagnosis:** Assisting doctors in diagnosing diseases based on patient data and symptoms.
        *   **Spam Detection:** Classifying emails as legitimate or spam.
        *   **Predictive Maintenance:** Predicting equipment failures in advance to schedule maintenance and prevent downtime.

*   Q112 - What is the Process of Data Mining / Knowledge Discovery Process?
    *   **A112:** The typical knowledge discovery in databases (KDD) process involves several steps:
        1.  **Data Cleaning:** Removing noise and inconsistent data.
        2.  **Data Integration:** Combining data from multiple sources.
        3.  **Data Selection:** Retrieving relevant data from the database.
        4.  **Data Transformation:** Transforming data into appropriate forms for mining.
        5.  **Data Mining:** Applying intelligent methods to extract patterns.
        6.  **Pattern Evaluation:** Identifying truly interesting patterns.
        7.  **Knowledge Presentation:** Visualizing and presenting the discovered knowledge.

*   Q113 - What are the Challenges of Data Mining?
    *   **A113:**
        *   **Data Quality:** Dealing with incomplete, noisy, and inconsistent data.
        *   **Scalability:** Handling massive datasets efficiently.
        *   **Complexity of Data:** Mining complex data types (e.g., spatial, temporal, multimedia).
        *   **Privacy and Security:** Protecting sensitive information during data mining.
        *   **Interpretability of Results:** Making the discovered patterns understandable and actionable.
        *   **Overfitting:** Building models that perform well on training data but poorly on unseen data.

*   Q114 - What is Machine Learning?
    *   **A114:** Machine learning is a subset of artificial intelligence (AI) that enables systems to learn from data, identify patterns, and make decisions with minimal human intervention. It focuses on the development of computer programs that can access data and use it to learn for themselves.

*   Q115 - What is Deep Learning?
    *   **A115:** Deep learning is a subfield of machine learning that uses artificial neural networks with multiple layers (deep neural networks) to learn from large amounts of data. It is particularly effective for tasks involving unstructured data like images, audio, and text.

*   Q116 - What are the data mining tasks / algorithms?
    *   **A116:** Common data mining tasks and their associated algorithms include:
        *   **Classification:** Decision Trees, Support Vector Machines (SVM), Naive Bayes, K-Nearest Neighbors (KNN), Logistic Regression.
        *   **Clustering:** K-Means, DBSCAN, Hierarchical Clustering.
        *   **Association Rule Mining:** Apriori, Eclat.
        *   **Regression:** Linear Regression, Polynomial Regression, Ridge Regression, Lasso Regression.
        *   **Anomaly Detection:** Isolation Forest, One-Class SVM.

*   Q117 - What is the difference between Classification and Clustering?
    *   **A117:**
        *   **Classification:** A supervised learning task where the goal is to predict a categorical label for new data points based on a labeled training dataset. (e.g., spam or not spam, disease or no disease).
        *   **Clustering:** An unsupervised learning task where the goal is to group similar data points together into clusters without any prior knowledge of labels. (e.g., customer segmentation, document categorization).

*   Q118 - Provide examples of clustering algorithms.
    *   **A118:**
        *   K-Means Clustering
        *   DBSCAN (Density-Based Spatial Clustering of Applications with Noise)
        *   Hierarchical Clustering
        *   Mean-Shift
        *   Gaussian Mixture Models (GMM)

*   Q119 - Provide examples of classification algorithms.
    *   **A119:**
        *   Logistic Regression
        *   Decision Trees
        *   Random Forest
        *   Support Vector Machines (SVM)
        *   K-Nearest Neighbors (KNN)
        *   Naive Bayes
        *   Gradient Boosting (e.g., XGBoost, LightGBM)

*   Q120 - What is an association rule?
    *   **A120:** An association rule is a data mining technique used to discover relationships between variables in large databases. It identifies frequent co-occurring items or events. A common application is market basket analysis (e.g., "customers who buy bread also buy milk").

*   Q121 - How do common machine learning algorithms work (e.g., K-Means, Regression, SVM, Decision Tree, KNN)?
    *   **A121:**
        *   **K-Means:** An unsupervised clustering algorithm that partitions data into K clusters. It iteratively assigns data points to the nearest cluster centroid and then updates the centroids based on the mean of the assigned points.
        *   **Regression (e.g., Linear Regression):** A supervised learning algorithm used for predicting a continuous target variable. Linear regression finds the best-fitting straight line through the data to model the relationship between independent and dependent variables.
        *   **Support Vector Machine (SVM):** A supervised learning algorithm used for classification and regression. It finds an optimal hyperplane that best separates data points into different classes with the largest margin.
        *   **Decision Tree:** A supervised learning algorithm that uses a tree-like model of decisions and their possible consequences. It splits the data into subsets based on features, creating a tree structure where each internal node represents a test on an attribute, each branch represents an outcome of the test, and each leaf node represents a class label.
        *   **K-Nearest Neighbors (KNN):** A non-parametric, supervised learning algorithm used for classification and regression. It classifies a new data point based on the majority class of its 'k' nearest neighbors in the feature space.

*   Q122 - What are recall, precision, and F1-score?
    *   **A122:** These are common metrics used to evaluate the performance of classification models:
        *   **Precision:** The ratio of correctly predicted positive observations to the total predicted positive observations. (TP / (TP + FP)). It answers: "Of all the instances predicted as positive, how many were actually positive?"
        *   **Recall (Sensitivity):** The ratio of correctly predicted positive observations to all observations in the actual class. (TP / (TP + FN)). It answers: "Of all the actual positive instances, how many did we correctly predict?"
        *   **F1-Score:** The harmonic mean of Precision and Recall. It tries to find the balance between precision and recall. (2 * (Precision * Recall) / (Precision + Recall)). It's useful when you need to balance both precision and recall, especially with uneven class distributions.
        *   *TP = True Positive, FP = False Positive, FN = False Negative*

*   Q123 - What is the bias-variance trade-off?
    *   **A123:** The bias-variance trade-off is a central concept in machine learning. It refers to the dilemma of simultaneously minimizing two sources of error that prevent supervised learning algorithms from generalizing beyond their training data:
        *   **Bias:** The error introduced by approximating a real-world problem (which may be complicated) by a simplified model. High bias can cause an algorithm to miss the relevant relations between features and target outputs (underfitting).
        *   **Variance:** The error introduced from the model's sensitivity to small fluctuations in the training data. High variance can cause an algorithm to model the random noise in the training data, rather than the intended outputs (overfitting).
        *   The goal is to find a balance where the model is complex enough to capture the underlying patterns (low bias) but not so complex that it fits the noise in the training data (low variance).

*   Q124 - What is a confusion matrix?
    *   **A124:** A confusion matrix is a table that is often used to describe the performance of a classification model on a set of test data for which the true values are known. It allows visualization of the performance of an algorithm. Each row of the matrix represents the instances in an actual class, while each column represents the instances in a predicted class.

*   Q125 - What is the ROC Curve?
    *   **A125:** An ROC (Receiver Operating Characteristic) curve is a graph showing the performance of a classification model at all classification thresholds. It plots two parameters:
        *   True Positive Rate (TPR) or Recall
        *   False Positive Rate (FPR)
        An ROC curve plots TPR vs. FPR at different classification thresholds. The Area Under the Curve (AUC) is a measure of the ability of a classifier to distinguish between classes and is used as a summary of the ROC curve.

*   Q126 - Explain cross-validation.
    *   **A126:** Cross-validation is a technique used to evaluate the performance of a machine learning model and to assess how well it generalizes to an independent dataset. The most common type is K-fold cross-validation, where the dataset is divided into K equal-sized folds. The model is trained K times, each time using K-1 folds for training and one fold for testing. The results are then averaged to get a more robust estimate of the model's performance.

*   Q127 - What is the difference between a validation set and a test set?
    *   **A127:**
        *   **Training Set:** The portion of the data used to train the machine learning model.
        *   **Validation Set:** A separate portion of the data used to tune the hyperparameters of the model and to evaluate the model's performance during training. It helps in preventing overfitting.
        *   **Test Set:** A completely independent portion of the data that is used to evaluate the final performance of the trained and tuned model. It provides an unbiased evaluation of the model's generalization ability.

*   Q128 - How do you treat missing values in data?
    *   **A128:** Handling missing values is a crucial step in data preprocessing:
        *   **Deletion:**
            *   **Row-wise deletion:** Remove entire rows containing any missing values. (Suitable for small number of missing values).
            *   **Column-wise deletion:** Remove entire columns if they have a high percentage of missing values.
        *   **Imputation:** Replacing missing values with estimated ones:
            *   **Mean/Median/Mode Imputation:** Replace with the mean (for numerical), median (for skewed numerical), or mode (for categorical) of the respective column.
            *   **Forward Fill/Backward Fill:** Propagate the last valid observation forward or next valid observation backward.
            *   **Regression Imputation:** Predict missing values using a regression model based on other features.
            *   **K-Nearest Neighbors (KNN) Imputation:** Impute missing values based on the values of the K-nearest neighbors.

*   Q129 - How do you prepare the data for the ML Model?
    *   **A129:** Data preparation is a critical step before training an ML model:
        1.  **Data Cleaning:** Handle missing values, outliers, and inconsistencies (as discussed in Q109 and Q128).
        2.  **Data Integration:** Combine data from various sources if necessary.
        3.  **Data Transformation:**
            *   **Normalization/Standardization:** Scaling numerical features to a standard range (e.g., 0-1 or mean 0, std dev 1) to prevent features with larger values from dominating.
            *   **Feature Engineering:** Creating new features from existing ones to improve model performance.
            *   **Encoding Categorical Variables:** Converting categorical data into numerical format (e.g., One-Hot Encoding, Label Encoding).
        4.  **Data Reduction:** Reducing the dimensionality of the data (e.g., PCA) or sampling to handle large datasets.
        5.  **Data Splitting:** Dividing the data into training, validation, and test sets.

## Statistics (Data Science Track)

*   Q130 - What are Mean, Median, and Mode?
    *   **A130:** These are measures of central tendency, used to describe the center point of a dataset:
        *   **Mean:** The average of all values in a dataset. Calculated by summing all values and dividing by the number of values. (Sensitive to outliers).
        *   **Median:** The middle value in a dataset when the values are arranged in ascending or descending order. If there's an even number of values, it's the average of the two middle values. (Robust to outliers).
        *   **Mode:** The value that appears most frequently in a dataset. A dataset can have one mode (unimodal), multiple modes (multimodal), or no mode.

*   Q131 - What is a Box Plot?
    *   **A131:** A box plot (or box-and-whisker plot) is a standardized way of displaying the distribution of data based on a five-number summary: minimum, first quartile (Q1), median (Q2), third quartile (Q3), and maximum. It can also indicate outliers.
        *   The "box" represents the interquartile range (IQR = Q3 - Q1), with a line inside for the median.
        *   The "whiskers" extend from the box to the minimum and maximum values within 1.5 times the IQR.
        *   Points beyond the whiskers are considered outliers.

*   Q132 - What are the types of skewed data?
    *   **A132:** Skewness refers to the asymmetry of a distribution.
        *   **Positive Skew (Right-skewed):** The tail of the distribution extends to the right, and the majority of the data is concentrated on the left. Mean > Median > Mode.
        *   **Negative Skew (Left-skewed):** The tail of the distribution extends to the left, and the majority of the data is concentrated on the right. Mean < Median < Mode.
        *   **Symmetric (Zero Skew):** The data is evenly distributed around the mean, with no tail on either side. Mean ≈ Median ≈ Mode (e.g., normal distribution).

*   Q133 - What is the Pearson correlation coefficient?
    *   **A133:** The Pearson correlation coefficient (often denoted as 'r') is a measure of the linear correlation between two sets of data. It is a value between -1 and +1 inclusive, where:
        *   +1 indicates a perfect positive linear correlation.
        *   -1 indicates a perfect negative linear correlation.
        *   0 indicates no linear correlation.
        It measures the strength and direction of a linear relationship between two variables.

*   Q134 - What is A/B Testing?
    *   **A134:** A/B testing (also known as split testing) is a randomized controlled experiment used to compare two versions of a single variable (A and B) to determine which one performs better. It's commonly used in marketing, web design, and product development to test changes to user interfaces, features, or content and measure their impact on user behavior. Users are randomly assigned to either group A (control) or group B (variant), and their interactions are measured and compared statistically.
