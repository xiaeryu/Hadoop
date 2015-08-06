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


Data Type
---
* **TINYINT** — 1 byte integer (Boolean)
* **SMALLINT** — 2 byte integer
* **INT** — 4 byte integer
* **BIGINT** — 8 byte integer
* **DOUBLE** — Double precision floating point
* **STRING** — Sequence of characters
