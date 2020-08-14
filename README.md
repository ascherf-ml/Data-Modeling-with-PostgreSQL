# Data Modeling with Postgres

The task of this project is to help the analytics team to understand what songs users are listening to. 
Because the data is separated into song files and log files from users, it is necessary to first create tables from the raw data.
The schema is in this case a star schema with the 'songplays' fact table in the middle and different dimension tables providing supplementary information (users table, songs table, artists table and a time table).

First I created the different tables.

### Fact Table 
___________________
**songplays**
Consists of records in log data associated with song plays.

- songplay_id (INT) PRIMARY KEY: ID of each song play per user
- start_time (DATE): Timestamp
- user_id (INT)
- level (TEXT): User level paid or free
- song_id (TEXT)
- artist_id (TEXT)
- session_id (INT): Session ID per user
- location (TEXT): User location
- user_agent (TEXT): Access to app

### Dimension Tables
_________________
**users**
Users in database

- user_id (INT) PRIMARY KEY
- first_name (TEXT)
- last_name (TEXT)
- gender (TEXT)
- level (TEXT): User level paid or free

________________
**songs** 
Songs in database

- song_id (TEXT) PRIMARY KEY
- title (TEXT)
- artist_id (TEXT)
- year (INT): Year of song release
- duration (FLOAT): Song duration

___________________
**artists** 
Artists in database

- artist_id (TEXT) PRIMARY KEY
- name (TEXT): Name of Artist
- location (TEXT): Name of artist' city
- latitude (FLOAT): Latitude location of artist
- longitude (FLOAT): Longitude location of artist

__________________
**time**
Timestamps of records

- start_time (DATE) PRIMARY KEY: Timestamp
- hour (INT): Hour of start_time
- day (INT): Day of start_time
- week (INT): Week of start_time
- month (INT): Month of start_time
- year (INT): Year of start_time
- weekday (TEXT): Name of day of start_time

__________________

## File Structure
**Files used on the project:**

sql_queries.py contains all sql queries
create_tables.py drops and creates tables.
etl.py reads and processes files from song_data and log_data and loads them into tables.

## Project Running Order

1. Run in console
*%run create_tables.py*
2. Run Notebook
"test.ipynb"
Verify, that all tables are created properly
3. Run in console
*%run etl.py*
Verify, that all the JSON files are properly processed.
4. (Optional) Run Notebook
"test.ipynb"
Verify, that all the tables have values properly inserted into them.


