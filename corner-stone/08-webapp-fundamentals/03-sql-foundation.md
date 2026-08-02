## Introduction to Databases
Databases are basically an organised collection of structured info thats easy to access and can be manipulated or analysed. This data can be all kinds of stuff like login credentials that get checked during authentication, or user generated content on social media like posts comments and likes, or even watch history on streaming platforms thats used to build recommendations. Its not just huge companies using these either, even small businesses setting up will almost always need some kind of database to store their data

## Types of Databases
There are two primary types worth focusing on as a beginner, relational aka SQL and non relational aka NoSQL

Relational databases store structured data meaning whatever gets inserted has to follow a defined structure, like a user record always having first_name last_name email_address username and password. This structured data sits in rows and columns inside tables, and relationships can be built between different tables like connecting a user table to an order_history table, thats where the name relational comes from

Non relational databases store data in a non tabular format instead. This works well when data varies a lot in type and quantity, like scanned documents. An example would look something like an object with fields like name date_of_birth occupation and steps_taken, no fixed table structure required

Choosing between the two depends on context. Relational makes more sense when data comes in consistently and accuracy matters like ecommerce transactions, non relational makes more sense when data format varies a lot but still needs to be collected in one place like social media content

## Tables Rows and Columns
All data in a relational database lives inside tables, like a bookstore might have a table called Books to store its inventory. When creating a table you define what pieces of info make up a record, these become your columns, and each column also gets a defined data type, if you try inserting data that doesnt match that type it gets rejected

Common data types across most databases

- strings — collection of words and characters
- integers — whole numbers
- floats/decimals — numbers with a decimal point
- times/dates — date and time values

Once the table structure is defined the first actual record gets inserted, like a book named Android Security Internals with id 1 and publication date 2014-10-14, once inserted this becomes a row

## Primary and Foreign Keys
Once you have multiple tables you often need to relate them together, this is where keys come in

Primary key ensures the data in a column is unique, its how you identify each record in a table without any duplicates, kinda like matriculation numbers for university students since names can repeat but numbers dont. In a books table id makes the most sense as the primary key since titles or dates could technically repeat but the id wont. Only one primary key column is allowed per table

Foreign key is a column that also exists in another table, creating a link between the two. Like adding an author_id column to the Books table which corresponds to the id column in an Authors table, this is what makes relationships between tables actually work. A table can have more than one foreign key column

## What is SQL
Databases are usually controlled through a DBMS or Database Management System, its the software that sits between the user and the database letting you retrieve update and manage data. Examples of DBMS include MySQL MongoDB Oracle Database and MariaDB

SQL or Structured Query Language is how we actually interact with a relational database through a DBMS, its used to query define and manipulate the data stored inside it

Some benefits that make SQL worth learning

- fast — relational databases return huge batches of data almost instantly due to efficient storage and high processing speed
- easy to learn — written in plain english so its way more readable than most programming languages
- reliable — enforces a strict structure on data before it can even be inserted which keeps accuracy high
- flexible — gives a lot of capability for querying which makes data analysis tasks efficient

To connect to mysql you run `mysql -u root -p` then enter the password when prompted, once connected you get the mysql prompt ready to take commands

## Database Statements
CREATE DATABASE is the first step when you need a new database, syntax is `CREATE DATABASE database_name;` so for this lesson we ran `CREATE DATABASE thm_bookmarket_db;`

SHOW DATABASES lists all the databases currently present using `SHOW DATABASES;`, alongside the one you just made youll also see default ones like mysql information_scheme performance_scheme and sys which mysql needs internally to function

USE DATABASE tells mysql which database to run your next queries against, done with `USE thm_bookmarket_db;`

DROP DATABASE removes a database entirely when its no longer needed, syntax is `DROP database database_name;`

## Table Statements
CREATE TABLE is used once a database is active, you define the table name along with each column and its data type inside brackets. Example used in the lesson

```sql
CREATE TABLE book_inventory (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    book_name VARCHAR(255) NOT NULL,
    publication_date DATE
);
```

Book_id is an INT with AUTO_INCREMENT so it assigns 1 to the first book 2 to the second and so on, and its set as PRIMARY KEY since every table needs one to uniquely identify records. Book_name uses VARCHAR(255) meaning variable characters up to 255 with NOT NULL meaning it cant be left empty. Publication_date just uses the DATE type

SHOW TABLES lists the tables inside whatever database is currently active using `SHOW TABLES;`

DESCRIBE or DESC shows the columns of a table along with their data types, ran as `DESCRIBE book_inventory;` which gives back a breakdown showing field type null key default and extra for each column

ALTER lets you modify a table after its already created, like adding a new column. Example used to add a page count column

```sql
ALTER TABLE book_inventory
ADD page_count INT;
```

ALTER can also rename columns change data types or remove columns entirely

DROP removes a table completely using `DROP TABLE table_name;`

## CRUD Operations
CRUD stands for Create Read Update Delete, these are the basic operations for managing data in any system. All these examples use the books table inside thm_books, accessed with `use thm_books;`

Create uses INSERT INTO to add a new record

```sql
INSERT INTO books (id, name, published_date, description)
VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");
```

Read uses SELECT to fetch data, `SELECT * FROM books;` grabs every column, while `SELECT name, description FROM books;` grabs only the specified columns instead of everything

Update uses UPDATE combined with SET and WHERE to modify existing records

```sql
UPDATE books
SET description = "An In-Depth Guide to Android's Security Architecture."
WHERE id = 1;
```

Delete uses DELETE FROM combined with WHERE to remove records

```sql
DELETE FROM books WHERE id = 1;
```

Quick summary of the four

- INSERT — adds a new record
- SELECT — retrieves records
- UPDATE — modifies existing data
- DELETE — removes records

## Clauses
A clause specifies criteria for the data being manipulated, helping define what data to grab and how to sort or filter it. FROM and WHERE are clauses we already used earlier, this section covers DISTINCT GROUP BY ORDER BY and HAVING, still using the books table from thm_books

DISTINCT avoids duplicate results and returns only unique values, so instead of Ethical Hacking showing up twice with a plain `SELECT * FROM books;`, running `SELECT DISTINCT name FROM books;` collapses it down to just one instance

GROUP BY aggregates data from multiple records and groups results by column, useful alongside aggregate functions. Example `SELECT name, COUNT(*) FROM books GROUP BY name;` groups by name and shows Ethical Hacking with a count of 2 since it appears twice

ORDER BY sorts results in ascending or descending order using ASC or DESC. `ORDER BY published_date ASC;` sorts oldest to newest, `ORDER BY published_date DESC;` sorts newest to oldest

HAVING filters grouped results after aggregation happens, different from WHERE which filters before aggregation. Example `SELECT name, COUNT(*) FROM books GROUP BY name HAVING name LIKE '%Hack%';` only returns grouped results where the name contains the word Hack

## Operators
This section uses the books table from thm_books2, accessed with `use thm_books2;`

Logical operators test a condition and return true or false

- LIKE — filters for a pattern within a column, like `WHERE description LIKE "%guide%";` to find descriptions containing guide
- AND — returns true only if all conditions are true, like matching both category and name at once
- OR — returns true if at least one condition is true, like matching names containing either Android or iOS
- NOT — reverses a boolean condition, like excluding descriptions that contain guide
- BETWEEN — checks if a value falls within a range, like `WHERE id BETWEEN 2 AND 4;`

Comparison operators check how values relate to each other

- = — checks if values are equal, like matching an exact book name
- != — checks if values are not equal, like excluding a specific category
- < — checks if a value is less than the given one, like books published before 2020-01-01
- > — checks if a value is greater than the given one, like books published after 2020-01-01
- <= — checks if a value is less than or equal to the given one
- >= — checks if a value is greater than or equal to the given one

## Functions
String functions perform operations on text and return a value

CONCAT() joins two or more strings together, like combining name and category into one readable sentence per row using `CONCAT(name, " is a type of ", category, " book.")`

GROUP_CONCAT() concatenates data from multiple rows into a single field, like grouping book names together per category separated by commas

SUBSTRING() pulls out part of a string starting at a set position with an optional length, like `SUBSTRING(published_date, 1, 4)` to just grab the year from a full date

LENGTH() returns how many characters are in a string including spaces and punctuation, useful for something like checking how long each book name is

Aggregate functions combine multiple row values into one result

- COUNT() — returns the number of records, like counting total books in the table
- SUM() — adds up all non null values in a column, like totaling up prices
- MAX() — returns the highest value in a column, like the most recent publication date
- MIN() — returns the lowest value in a column, like the earliest publication date

## Summary
Databases are organised collections of data thats easy to access manipulate and analyse. The two main types are relational for structured data and non relational for more flexible non tabular data. Relational databases are built from tables columns and rows, with primary keys keeping records unique and foreign keys linking tables together. SQL is the language used to interact with relational databases through a DBMS, and its considered fast reliable flexible and easy to pick up. Database and table statements let you create and manage the structure itself, CRUD operations let you manage the actual data, clauses let you filter sort and group results, and operators plus functions give you the tools to filter and manipulate data with more precision