Hive
===
Apache Hadoop subprojects
---
* **Pig**: A high-level data flow language
* **Hive**: A SQL-like data warehouse infrastructure
* **HBase**: A distributed, column-oriented database modeled after Google’s Bigtable
* **ZooKeeper**: A reliable coordination system for managing shared state between distributed applications
* **Chukwa**: A data collection system for managing large distributed systems

Interact with Hive
---
* Web GUI
* Java Database Connectivity (JDBC) interface
* Command line interface (CLI)

Hive commands
---
#### CREATE
```SQL
CREATE TABLE cite (citing INT, cited INT)
ROW FORMAT DELIMITED
FIELDS TERMINATED BY ','
STORED AS TEXTFILE;

LOAD DATA LOCAL INPATH 'cite75_99.txt'
OVERWRITE INTO TABLE cite;
```

#### SHOW TABLE
```SQL
SHOW TABLES;
```
Show what tables are currently in Hive.

#### DESCRIBE
```SQL
DESCRIBE alias;
```
Check schema.

#### SELECT
```SQL
SELECT [ALL | DISTINCT] select_expr, select_expr, ...
FROM table_reference
[WHERE where_condition]
[GROUP BY col_list]
[HAVING having_condition]
[CLUSTER BY col_list | [DISTRIBUTE BY col_list] [SORT BY col_list]]
[LIMIT number]
```

#### INSERT
```SQL
INSERT OVERWRITE TABLE tablename1 select_statement1 FROM from_statement;
INSERT INTO TABLE tablename1 select_statement1 FROM from_statement;
```
INSERT OVERWRITE will overwrite any existing data in the table.  
INSERT INTO will append to the table, keeping the existing data intact.

Data Type
---
* **TINYINT** — 1 byte integer (Boolean)
* **SMALLINT** — 2 byte integer
* **INT** — 4 byte integer
* **BIGINT** — 8 byte integer
* **DOUBLE** — Double precision floating point
* **STRING** — Sequence of characters
