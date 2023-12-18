# Set up SQL

After doing some research online to set up SQL locally, I managed to get it up an running. Creating a database is essential.

```sql
-- Database Creation 
CREATE DATABASE Cyclistic;

-- Remember use the databse
USE Cyclistic;
```

Then creating a table.

```sql
CREATE TABLE `202212-divvy` (
	ride_id VARCHAR(255),
	rideable_type MEDIUMTEXT,
	started_at DATETIME,
	ended_at DATETIME,
	start_station_name MEDIUMTEXT,
	start_station_id MEDIUMTEXT,
	end_station_name MEDIUMTEXT,
	end_station_id MEDIUMTEXT,
	start_lat DOUBLE,
	start_lng DOUBLE,
	end_lat DOUBLE,
	end_lng DOUBLE,
	member_casual MEDIUMTEXT
);
```

After that, I noticed the data importing wizard of SQL workbench is too slow, so I search around and find a way to import data from command prompt. 

## Import data through command prompt

* Step 1: Find the path of you bin folder in SQL server folder
Change current working directory to that folder in command prompt. In my case the it's C:\Program Files\MySQL\MySQL Server 8.0\bin

```shell
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```

* Step 2: Connect to mysql database

```shell
mysql -u root -p
```

* Step 3: Input the below code to enable loading data from a local file into mySQL table
```shell
SET GLOBAL local_infile=1;
```

* Step 4: After setting SET GLOBAL local_infile=1;, you need to reconnect to the server to apply the changes. Simply quit the server and reconnect
```shell
quit;
```
Then 
```shell
mysql --local-infile=1 -u root -p
```

* Step 5: Load the data into the table we created. I save my csv files in D:\New folder (9).
> Loading 202212-divvy.csv to the table 202212-divvy

```shell
LOAD DATA LOCAL INFILE 'D:\\New folder (9)\\202212-divvy.csv' 
INTO TABLE cyclistic.`202212-divvy` 
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"' 
LINES TERMINATED BY '\r\n' IGNORE 1 ROWS;
```

* Step 6: As I'm using 12 data set, I need to create 11 more tables in mySQL to import the dataset. Instead of repeating the first step, I use the code below:

```sql1
CREATE TABLE cyclistic.`202301-divvy` LIKE cyclistic.`202212-divvy`;
```
> I did the same with the rest, simply replacing 202301 with 202302, 202303 and beyond.




