## SQL

- relational database management language 
- database - structured form of data 

### Syntax:

- commands are written in all caps, e.g. SELECT
- queries are terminated with a ;
- comments: -- 

#### Statements:

- SELECT * FROM db - selects all entries
  - SELECT COUNT(*) - displays count of an indicated row
  - SELECT DISTINCT - only unique values
  - LIMIT x; - show only x values
- UPDATE - updates data, DELETE
- INSERT INTO
- CREATE DATABASE, TABLE
- ALTER DATABASE, TABLE
- DROP TABLE
- CREATE INDEX - index is a search key (can be unique, clustered or non-clustered)
- DELETE INDEX

#### Conditionals:

- SELECT * FROM db WHERE key=“value”;
- can be combined with AND, OR and NOT
- HAVING (filter by attribute)

#### Ordering and grouping:

- SELECT * FROM db ORDER BY val DESC (or ASC)
- can be combined (e.g. order by row 1 ascending and row 2 descending)
- GROUP BY r1

#### Creating and deleting:

```sql
CREATE TABLE t (
     id INT PRIMARY KEY,
     name VARCHAR NOT NULL,
     price INT DEFAULT 0
);
```

- DROP TABLE - removes from database

#### Adding and removing stuff:

- ```sql
  ALTER TABLE t ADD column;
  ```

- ```sql
  ALTER TABLE t DROP COLUMN c ;
  ```

- ```sql
  ALTER TABLE t ADD constraint;
  ```

- ```sql
  ALTER TABLE t1 RENAME TO t2;
  ```

- ```sql
  TRUNCATE TABLE t; --remove all data
  ```



#### Joining multiple tables:

- SELECT r1, r2 FROM t1 INNER JOIN t2 ON condition;
- INNER JOIN - only matching values in both
- OUTER JOIN - 
- LEFT JOIN - all records from left and matching from right
- RIGHT JOIN - all records from right and matching from left
- CROSS JOIN - paired combinations of rows from right and left

#### Operators:

	- IS [NOT] [NULL]
	- INTERSECT
	- [NOT] LIKE *pattern*
	- WHERE a BETWEEN low AND high



