# PostGreSQL commands
connecting to psql: `psql --username=your_username --dbname=postgres`
rebuilding database `psql -U postgres < dbname.sql`
dumping into .sql file `pg_dump -cC --insert -U username dbname > dbname.sql`
`\l` list all database available
`\d` print details of the database to cmd
`\d table_name` print details of the table in the database to cmd
`\c database_name` connects to a database

### CREATE DATABASE
`CREATE DATABASE database_name;`

### ALTER DATABASE
#### Rename database
`ALTER DATABASE database_name RENAME TO new_db_name;`

### CREATE TABLE
`CREATE TABLE table_name();`
`CREATE TABLE table_name(column_name VARTYPE CONSTRAINTS);` e.g. `CREATE TABLE sample(first_col INT PRIMARY KEY);`

### DROP TABLE
`DROP TABLE table_name`

### ALTER TABLE
#### Add column
`ALTER TABLE table_name ADD COLUMN column_name DATATYPE;`

***Add column and foreign key with it***
* `ALTER TABLE table_name ADD COLUMN column_name DATATYPE REFERENCES reference_table_name(reference_column_name);`
* `ALTER TABLE table_name ADD COLUMN column_name DATATYPE CONSTRAINT REFERENCES reference_table_name(reference_column_name);`

#### Rename column
`ALTER TABLE table_name RENAME COLUMN column_name TO new_name;`

#### Add primary key
`ALTER TABLE table_name ADD PRIMARY KEY(column_name);`

#### Drop column
`ALTER TABLE table_name DROP COLUMN column_name;`

#### Add constaraint to existing table
`ALTER TABLE table_name ADD CONSTRAINT constraint_name;`  

***Add unique:***
* `ALTER TABLE table_name ADD UNIQUE(column_name);`
* `ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE(column_name);`  

***Add primary key***
* `ALTER TABLE table_name ADD PRIMARY KEY(column_name)`;

***Set to NOT NULL***
* `ALTER TABLE table_name ALTER COLUMN column_name SET NOT NULL;`

***Add foreign key***
* `ALTER TABLE table_name ADD FOREIGN KEY(column_name) REFERENCES reference_table_name(reference_column_name);`

#### Drop constraints 
`ALTER TABLE table_name DROP CONSTRAINT constraint_name;`

#### Change datatypes for existing columns
`ALTER TABLE table_name ALTER COLUMN column_name TYPE new_data_type USING expression`
* `ALTER TABLE table_name ALTER COLUMN column_name TYPE VARCHAR`
* `ALTER TABLE table_name ALTER COLUMN column_name TYPE INT USING column_name::integer;`

### INSERT 
`INSERT INTO table_name(column_name, ..) VALUES(val1, val2, ..), ...;`

### UPDATE value in cols
`UPDATE table_name SET column_name=new_val WHERE condition;`

### SELECT
`SELECT column FROM table_name;`
***With Order***
`SELECT column FROM table_name ORDER BY column_name;`
* `ASC` order in ascending order
* `DESC` order in descending order

***With WHERE Condition***
`SELECT column FROM table_name WHERE condition;`

***With more than one condition***
use `OR` for or conditions, use `AND` for and conditions
`WHERE condition1 AND condition2 OR condition3`

***With Pattern Mathing***
`LIKE` finds data that match a pattern: `WHERE column LIKE pattern`. 
`NOT LIKE` find data that doesn't match with pattern: `WHERE column NOT LIKE pattern`
`ILIKE` find data that match a pattern ignoring Upper or lower cases.
`NOT ILIKE` find data that doesn't match pattern ignoring cases.

* `_` in pattern returns row that have any characters in that spot
* `%` means that anything can be in that position

***With null check***
`WHERE column IS NULL`

***With Join***
* **Full Join**: include all rows from both table `SELECT column FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.primary_key_column;` 

* **Left Join**: gets all rows from the left table, but only rows from the right table that are linked to from the left one. `SELECT column FROM table_1 LEFT JOIN table_2 ON table_1.primary_key_column = table_2.primary_key_column;`

* **Right Join**: gets all rows from the right table `SELECT column FROM table_1 RIGHT JOIN table_2 ON table_1.primary_key_column = table_2.primary_key_column;`

* **Inner Join**: it only returned rows if they have a value in the foreign key column of the opposite table `SELECT column FROM table_1 INNER JOIN table_2 ON table_1.primary_key_column = table_2.primary_key_column;`

* **Joining with USING**: instead of typing `table_1.key = table_2.key` simply do `SELECT * FROM table_1 FULL JOIN table_2 USING(column_in_common)`

***Return Certain number of rows***
`LIMIT number` put at the end of the query

***Count number of entries of a column***
`COUNT()`: this function counts. Doesn't count rows `SELECT COUNT(col) FROM table`

***Display unique ***
* `DISTINCT(column)`: returns row with distinct/unique values. `SELECT DISTINCT(col) FROM table`
* `GROUP BY`: `SELECT column FROM table GROUP BY column`
* `HAVING`: `SELECT column FROM table GROUP BY column HAVING condition`

***Changing column name when selected***
`AS`: `SELECT column AS column_new_name FROM...`

###### Numerical column mathematic functions
* `MIN`: find lowest value in the column `SELECT MIN(column) FROM table`
* `MAX`: find largest value in the column `SELECT MAX(column) FROM table`
* `SUM`: returns the sum of all values in the column `SELECT SUM(column) FROM table`
* `AVG`: returns the average of the values in the column `SELECT AVG(column) FROM table`
* `CEIL` rounds up decimal numbers `SELECT CEIL(col) FROM table`
* `FLOOR` rounds down decimal numbers `SELECT FLOOR(col) FROM table`
* `ROUND` rounds to the nearest number `SELECT ROUND(col) FROM table`. Use `ROUND(number, decimal_places)` to round a number to a desired decimal place


### DELETE
#### with conditions
`DELETE FROM table_name WHERE condition;`

## PSQL query from bash script
`psql -X --username=username --dbname=target_db_name --no-align --tuples-only -c` this command allows to query database from script. `-c` flag is for running a single command and exiting. 
`-X`, `--no-align`, `--tuples-only` are for formatting

Saving this in PSQL variable allows us to query using `$($PSQL "query")`



