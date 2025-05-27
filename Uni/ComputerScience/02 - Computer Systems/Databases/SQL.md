SQL is a Standard Querying Language for databases. SQL statements consist of reserved words (SELECT, WHERE, IS NOT NULL ...), user defined words/names (of relations, attributes etc.), and literals (string or numbers).
Most component are case insensitive except for table names and literals. Statements may be chained or terminated with a semicolon.

SELECT - specifies columns
FROM - Table(s) to query
WHERE - a condition to determine which rows to return
DISTINCT - eliminates duplicates (follows SELECT)
IN - set membership, equivalent to repeated OR statements
LIKE - used for pattern matching along with pattern-matching symbols
	% - WIld card, represents an arbitrary sequence of 0 or for characters.
		For example 'LIKE H%' will return elements starting with H
	 _  - Represents an arbitrary single character.
		 For example 'LIKE H_ _ _ ' will return 4 letter elements beginning with H
 ORDER BY - used to sort the rows according to the values of a set of columns, which do not need to appear in the result. ASC (default) for ascending and DESC for descending
 GROUP BY - used in combination with aggregate functions. It first groups rows by attributed and the aggregate functions are applied to each group separately.
 HAVING - like WHERE for aggreate functions

Aggregate functions operate on a single column and return a single value:
SUM - sum of numeric values in a column
AVG - average value of a given column
MIN - smallest value in a given column
MAX - largest value in a given column
COUNT - total number of values in a given column
COUNT(\*)number of rows in a table 

## JOINS
Joins are used to query multiple tables and combine into one result.
INNER JOIN ON <matching_criterion> - all matching combinations. 
LEFT [OUTER] JOIN ON <matching_criterion> - all matching combinations + missing records from left table.
RIGHT [OUTER] JOIN ON <matching_criterion> - all matching combinations + missing records from right table
FULL [OUTER] JOIN ON <matching_criterion> - all matching combinations + missing records from both tables

Format for a join: 
SELECT * 
FROM Table1 JOIN Table2 ON <matching_criterion> 
WHERE condition

## Nested Queries
You can nest a query inside another. For example:
SELECT *
FROM Table
WHERE condition = (SELECT * FROM AnotherTable WHERE another_condition)

For nested queries which return multiple values we use keywords SOME or ALL to make the WHERE condition true if it is satisfied by at least one / all values.

# Modifying Data
INSERT INTO TableName [(columnList)] VALUES (valueList)
UPDATE TableName SET columnName=dataValue [, ...] WHERE condition
DELETE FROM TableName WHERE condition


columnList is optional. If it is not specified then columns are enumerated in the order the table was created. If specified, valueList must match one to one with columnList

CREATE - Creates a new table and defines its schema, defines the names and domains of its attributes
ALTER - Changes a table structure
DROP - Deleted an entire Table
CREATE VIEW - virtual table/relation that appears to the user (useful for hiding information)

Domains: CHAR(n), VARCHAR(n), BIT(n), INTEGER, SMALLINT, NUMERIC(p,d). WE can also define our own custom domain types for specific needs. For example: CREATE DOMAIN Postcode AS VARCHAR(8)

We also specify a PRIMARY KEY and FOREIGN KEY and action for ON UPDATE and ON DELETE, out of the following: CASCADE (update foreign key/delete the tuple), SET NULL, SET DEFAULT, NO ACTION (may lead to inconsistencies)
