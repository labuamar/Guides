# Snowflake
Global data cloud network. Leverage cloud services
Multi-regional

Data platform that offers:

- Fast ingestion, transformation, retrieval
- Reliable, easy to use, minimal maintnance
- Accessable to anyone who needs it securely

# Dataset

The dataset for the guide is the popular Citi Bike dataset. Citi Bike is a citywide bike sharing system in NY city. 

In addition to that, we will test our hand at semi-structured JSON weather data to find correlation between the number of bike rides and the weather.

```
worksheet to run the DDL that creates the table. Copy the following SQL text into your worksheet:

create or replace table trips
(tripduration integer,
starttime timestamp,
stoptime timestamp,
start_station_id integer,
start_station_name string,
start_station_latitude float,
start_station_longitude float,
end_station_id integer,
end_station_name string,
end_station_latitude float,
end_station_longitude float,
bikeid integer,
membership_type string,
usertype string,
birth_year integer,
gender integer);
```


```
list @citibike_trips;
```



```
--create file format

create or replace file format csv type='csv'
  compression = 'auto' field_delimiter = ',' record_delimiter = '\n'
  skip_header = 0 field_optionally_enclosed_by = '\042' trim_space = false
  error_on_column_count_mismatch = false escape = 'none' escape_unenclosed_field = '\134'
  date_format = 'auto' timestamp_format = 'auto' null_if = ('') comment = 'file format for ingesting data for zero to snowflake';
```

```
--verify file format is created

show file formats in database citibike;
```
