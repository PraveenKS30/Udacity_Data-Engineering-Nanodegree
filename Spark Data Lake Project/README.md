### Introduction :

A music streaming startup, Sparkify, has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

To allow analytics team to continue finding insights in what songs the users are listening to, the task is to build an ETL pipeline that extracts their data from S3, processes them using Spark, and loads the data back into S3 as a set of dimensional tables.

### Methods :

**process_song_data :**
Processing performed in this method :

-Reading song json files.
-Create song and artist dataframes.
-Create song (partitioning by year and artist id) and artist parquet files.

```
**songs.parquet :** 'song_id', 'title', 'artist_id', 'year', 'duration'
**artists.parquet :** 'artist_id', 'artist_name', 'artist_location', 'artist_latitude', 'artist_longitude'
```
**process_log_data :**
Processing performed in this method:

-Reading log json files.
-Create users, time and songsplay dataframes.
-Write users, time and songplay dataframes in parquet files.

```
**users.parquet :** 'userId', 'firstName', 'lastName', 'gender', 'level'
**time_table.parquet :** 'start_time', 'hour', 'day', 'week', 'month', 'year', 'weekday'
**songplays_table.parquet :** 'start_time', 'userId', 'level', 'song_id', 'artist_id', 'sessionId', 'location', 'userAgent'
```
### Execution :
```
python elt.py
```
