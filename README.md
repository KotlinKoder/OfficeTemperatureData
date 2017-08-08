# OfficeTemperatureData
Raw data and processing code for analysis

## Table of content

Explanation of directories

### 01_rohsql

Scripts in this directory must be called in order of the prefix number.
The SQL dump will be imported and we will create a copy. Additional columns will be added.

### 02_geochecks

Scripts in this directory should be called according to the prefix number. Re-runs in arbitrary order are recommended. The scripts validates geolocation information and helps you to fill in missing values. 

Some scripts generate SQL and CSV files. Data in CSV files need to be processed manually.
Some generated SQL scripts might contain commented SQL statements in case of ambiguous results. You need to check the statements and values and resolve the ambiguity. 

```00_manual_fixes.sql``` contains additional SQL statements to fix geo location information. It is also used to store SQL statements created from CSV files.

### 03_climatedata

Scripts in this directory must be called in order of the prefix number.
The scripts download and import the weather date from the Deutschen Wetter Dienst (DWD).
Then the data is assigned to the values in the office temperature values.

Caution: The assignment will run several hours or even days depending on your hardware and MySQL settings. 

### 04_analysis

Except for the first two SQL scripts, the R scripts to generate statistics and charts can be called in any order.

## Recommended settings for MySQL

Requires at least 16 GByte RAM.

```
[mysqld]
general-log=0
innodb-buffer-pool-size=858993452
innodb-change-buffer-max-size=50
innodb-max-dirty-pages-pct=90
innodb-flush-log-at-trx-commit=0
max-heap-table-size=10737421824
secure_file_priv=
```