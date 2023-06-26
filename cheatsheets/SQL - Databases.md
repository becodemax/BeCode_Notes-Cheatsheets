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
