## sqlbolt.com

## Commands cheatsheet :

- Select and query data
```
SELECT column, another_column, … 
FROM mytable;
```

- Select query with constraint
```
SELECT column, another_column, … 
FROM mytable 
WHERE condition AND/OR another_condition AND/OR …;
```

- Operators for numerical data

|   |   |   |
|---|---|---|
|Operator|Condition|SQL Example|
|=, !=, < <=, >, >=|Standard numerical operators|col_name != 4|
|BETWEEN … AND …|Number is within range of two values (inclusive)|col_name BETWEEN 1.5 AND 10.5|
|NOT BETWEEN … AND …|Number is not within range of two values (inclusive)|col_name NOT BETWEEN 1 AND 10|
|IN (…)|Number exists in a list|col_name IN (2, 4, 6)|
|NOT IN (…)|Number does not exist in a list|col_name NOT IN (1, 3, 5)|

- Operators for strings and patterns

|   |   |   |
|---|---|---|
|Operator|Condition|Example|
|=|Case sensitive exact string comparison (_notice the single equals_)|col_name = "abc"|
|!= or <>|Case sensitive exact string inequality comparison|col_name != "abcd"|
|LIKE|Case insensitive exact string comparison|col_name LIKE "ABC"|
|NOT LIKE|Case insensitive exact string inequality comparison|col_name NOT LIKE "ABCD"|
|%|Used anywhere in a string to match a sequence of zero or more characters (only with LIKE or NOT LIKE)|col_name LIKE "%AT%"  <br>(matches "AT", "ATTIC", "CAT" or even "BATS")|
|'underscore'|Used anywhere in a string to match a single character (only with LIKE or NOT LIKE)|col_name LIKE "AN_"  <br>(matches "AND", but not "AN")|
|IN (…)|String exists in a list|col_name IN ("A", "B", "C")|
|NOT IN (…)|String does not exist in a list|col_name NOT IN ("D", "E", "F")|

- Select query with ordered results
```
SELECT column, another_column, … 
FROM mytable WHERE _condition(s)_
ORDER BY column ASC/DESC;
```

- Select query with limited rows
```
SELECT column, another_column, … 
FROM mytable WHERE _condition(s)_ 
ORDER BY column ASC/DESC 
LIMIT num_limit OFFSET num_offset;
```

- Select query on multiple tables
```
SELECT column, another_table_column, … 
FROM mytable 
INNER JOIN another_table 
	ON mytable.id = another_table.id
WHERE _condition(s)_ 
ORDER BY column, … ASC/DESC 
LIMIT num_limit OFFSET num_offset;
```

- LESSON 7 EXPLAINED : Select multiple queries through multiple tables
```
SELECT distinct building_name, role
from buildings
    left join employees
        on building = building_name

Explications :

- "building_name" appartient au tableau "Buildings"
- "role" appartient au tableau "Employees"
- "from buildings" : on traite les informations à partir du tableau "buildings" pour aussi obtenir, en sortie, les bâtiments vides.
- "left join employees on building = building_name" : on associe les valeurs de la colonne "building" du tableau "employees" aux valeurs de la colonne "building_name" du tableau "buildings".
```

- Select query with NULL values
```
SELECT column, another_column, … 
FROM mytable 
WHERE column IS/IS NOT NULL
AND/OR _another_condition_ AND/OR …;
```

- LESSON 9 : Queries with expressions
```
SELECT distinct title, (domestic_sales + international_sales) / 1000000 AS sum
FROM movies
    left join boxoffice
        on movies.id = boxoffice.movie_id
;

SELECT id, title, movie_id, rating * 10 AS ratings
FROM movies
    left join boxoffice
        on id = movie_id
;

SELECT title, year%2 AS even
FROM movies
where even = 0
;
```

- LESSON 10 : Aggregations queries

| Function                      | Description                                                                                                                                                                                                      |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| COUNT( * ) ,  COUNT( column ) | A common function used to counts the number of rows in the group if no column name is specified.                  Otherwise, count the number of rows in the group with non-NULL values in the specified column. |
| MIN( column )                 | Finds the smallest numerical value in the specified column for all rows in the group.                                                                                                                            |
| MAX( column )                 | Finds the largest numerical value in the specified column for all rows in the group.                                                                                                                             |
| AVG( column )                 | Finds the average numerical value in the specified column for all rows in the group.                                                                                                                             |
| SUM( column )                 | Finds the sum of all numerical values in the specified column for the rows in the group.                                                                                                                         |

```
SELECT distinct name, max(years_employed)
FROM employees
;

SELECT distinct role, avg(years_employed)
FROM employees
group by role
;

SELECT building, sum(years_employed)
FROM employees
group by building
;
```

- Lessons 11 : Aggregations (part 2)
```
SELECT count(role) 
FROM employees
where role = "Artist"
;

SELECT role, count(name)
FROM employees
group by role
;

SELECT role, sum(years_employed)
FROM employees
where role = "Engineer"
;
```

## Query : Order Of Execution

1. FROM and JOIN
2. WHERE
3. GROUP BY
4. HAVING
5. SELECT
6. DISTINCT
7. ORDER BY
8. LIMIT / OFFSET

```
Complete SELECT query

SELECT DISTINCT column, AGG_FUNC(column_or_expression), … 
FROM mytable 
	JOIN another_table ON mytable.column = another_table.column 
	WHERE constraint_expression
	GROUP BY column 
	HAVING constraint_expression
	ORDER BY column ASC/DESC 
	LIMIT count OFFSET COUNT;
```

- LESSON 12 : Complete query
```
SELECT count(title), director 
FROM movies
    group by director
;

select director, sum(domestic_sales + international_sales) AS total
from movies
    left join boxoffice on id = movie_id
    group by director
;
```

- LESSON 13 : Inserting data
```
insert into movies
(title, director, year, length_minutes)
values ("Toy Story 4", "Hitler", 2023, 120);

insert into boxoffice
(movie_id, rating, domestic_sales, international_sales)
values (15, 8.7, 340000000, 270000000);
```

- LESSON 14 : Update data
```
update movies
set director = "John Lasseter"
    where title = "A Bug's Life"
;

update movies
set year = 1999
    where title = "Toy Story 2"
;

update movies
set title = "Toy Story 3",
    director = "Lee Unkrich"
where title = "Toy Story 8"
;
```

- LESSON 15 : Delete data
```
delete from movies
where year < 2005;

delete from movies
where director = "Andrew Stanton";
```

- LESSON 16 : Creating tables
```
CREATE TABLE IF NOT EXISTS mytable ( 
	column _DataType_ _TableConstraint_ DEFAULT _default_value_, 
	another_column _DataType_ _TableConstraint_ DEFAULT _default_value_, … 
	);`
```

|   |   |
|---|---|
|Data type|Description|
|`INTEGER`, `BOOLEAN`|The integer datatypes can store whole integer values like the count of a number or an age. In some implementations, the boolean value is just represented as an integer value of just 0 or 1.|
|`FLOAT`, `DOUBLE`, `REAL`|The floating point datatypes can store more precise numerical data like measurements or fractional values. Different types can be used depending on the floating point precision required for that value.|
|`CHARACTER(num_chars)`, `VARCHAR(num_chars)`, `TEXT`|The text based datatypes can store strings and text in all sorts of locales. The distinction between the various types generally amount to underlaying efficiency of the database when working with these columns.<br><br>Both the CHARACTER and VARCHAR (variable character) types are specified with the max number of characters that they can store (longer values may be truncated), so can be more efficient to store and query with big tables.|
|`DATE`, `DATETIME`|SQL can also store date and time stamps to keep track of time series and event data. They can be tricky to work with especially when manipulating data across timezones.|
|`BLOB`|Finally, SQL can store binary data in blobs right in the database. These values are often opaque to the database, so you usually have to store them with the right metadata to requery them.|

|   |   |
|---|---|
|Constraint|Description|
|`PRIMARY KEY`|This means that the values in this column are unique, and each value can be used to identify a single row in this table.|
|`AUTOINCREMENT`|For integer values, this means that the value is automatically filled in and incremented with each row insertion. Not supported in all databases.|
|`UNIQUE`|This means that the values in this column have to be unique, so you can't insert another row with the same value in this column as another row in the table. Differs from the `PRIMARY KEY` in that it doesn't have to be a key for a row in the table.|
|`NOT NULL`|This means that the inserted value can not be `NULL`.|
|`CHECK (expression)`|This allows you to run a more complex expression to test whether the values inserted are valid. For example, you can check that values are positive, or greater than a specific size, or start with a certain prefix, etc.|
|`FOREIGN KEY`|This is a consistency check which ensures that each value in this column corresponds to another value in a column in another table.  <br>  <br>For example, if there are two tables, one listing all Employees by ID, and another listing their payroll information, the `FOREIGN KEY` can ensure that every row in the payroll table corresponds to a valid employee in the master Employee list.|

```
create table database (
    Name text,
    Version float,
    Download_count int
);
```

- LESSON 17 : Altering Tables
```
ALTER TABLE mytable 
	ADD column _DataType_ _OptionalTableConstraint_ 
		DEFAULT default_value;

ALTER TABLE mytable 
DROP column_to_be_deleted;

ALTER TABLE mytable 
RENAME TO new_table_name;
```

```
alter table movies
    add Aspect_ratio float
;

alter table movies
    add Language text
        default "English"
;
```

- LESSON 18 : Removing Tables
```
DROP TABLE IF EXISTS table;
```