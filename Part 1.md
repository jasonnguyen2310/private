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

* Find the path of you bin folder in SQL workbench folder
* Change current working directory to that folder in command prompt

```shell
cd C:\Program Files\MySQL\MySQL Server 8.0\bin
```
