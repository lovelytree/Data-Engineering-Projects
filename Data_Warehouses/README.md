# Data Warehouse



## Overview

A music streaming startup, Sparkify, has grown their user base and song database and want to move their processes and data onto the cloud. Their data reside in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs.

In this project, we will build an ETL pipeline that extracts data from S3, stages them in Redshift, and transforms data into a set of dimensional tables for their analytics team to continue finding insights in what songs their users are listening to.

## DataSets

#### Song Dataset
 - A subset of real data from the Million Song Dataset website; 
 - Each file is JSON format and contains metadata and artist of that song. 
 - Example of song file:

``` 
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```

#### Log Datasets
 - Log files is generated by an [event simulator](https://github.com/Interana/eventsim), with JSON format 
 - Example of log file
```
{"artist":"Line Renaud", "auth":"Logged In", "firstName":"Jayden", "gender":"M", "itemInSession":0, "lastName":"Fox", "length":152.92036, "level":"free", "location":"New Orleans-Metairie,LA", "method":"PUT", "page":"NextSong", "registration":1541033612796.0, "sessionId":184,"song":"Der Kleine Dompfaff", "status":200, "ts":1541121934796, "userAgent":"\"Mozilla\/5.0 ","userId":"101"}
```

## Schema for Song Play Analysis

### Staging Table:
* **staging_events**
* **staging_songs**

### Fact Table:
- **songplays** - records in log data associated with song plays i.e. records with page NextSong
```
  songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
```
### Dimension Table:
- **users** - users in the app
```
  user_id, first_name, last_name, gender, level
```
- **songs** - songs in music database
```
  song_id, title, artist_id, year, duration
```
- **artists** - artists in music database
``` 
  artist_id, name, location, latitude, longitude
```
- **time** - timestamps of records in songplays broken down into specific units
``` 
  start_time, hour, day, week, month, year, weekday
```

## Project File Structure

- `sql_queries.py` : contains all the sql queries 
- `create_tables.py` : drops and creates staging, fact and dimension tables
- `etl.py` : load data from s3 to staging table in Redshift, then process that data into analytics tables on Redshift
- `README.md` : provides discussion on your project.


## How to Run

- Launch a redshift cluster and create an IAM role that has read access to S3
- Add redshift database and IAM role info to dwh.cfg
- create tables:

```
python create_tables.py
```
- Load data from s3 to Redshift:

```
python etl.py
```

