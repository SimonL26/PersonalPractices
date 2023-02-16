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
***With Condition***
`SELECT column FROM table_name WHERE condition;`
***With Full Join***
`SELECT column FROM table_1 FULL JOIN table_2 ON table_1.primary_key_column = table_2.primary_key_column;`

### DELETE
#### with conditions
`DELETE FROM table_name WHERE condition;`





