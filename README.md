---
title: 'Data Modeling with Postgres'
---

Data Modeling with Postgres
===

## Table of Contents

[TOC]

## Overall

That is the brief of the project

* Sparkify is the star schema with fact table of songplays and dimension tables of songs, users, artists, and time.

* Analytic goals
    * With this model, the analyst can query to extract the information about how many times the song played. 
    * It can provide the information about user preferences. 
    * The artists can know what their song is listened the most.
    * The data team can use it to create a machine learning model for recommendation system.   
    
## How to run:
* Set up postgres database (Docker prefered)
* Install python, jupyter notebook, and dependencies (Pandas, Numpy...)
* Run create_tables.py
* Run etl.py
* Run cells in test.ipynd to see the result

## File explainations:

| File              | Explaination            |
| ----------------- |:----------------------- |
| create_tables.py       | This is a script to create sparkify schema and tables for fact and dimensions  |
| elt.py | This is a pipeline script to extract data from data folder, process data and load to database      |
| etl.ipynd         | This is a notebook to create functions for ETL pipeline    |
| sql_queries        | This file contains all queries to interact with database    | 
| test.ipynd   | This notebook to test data from database and check the quality of data |

User story
---
* Songplays table: 
    ```sql=
    CREATE TABLE IF NOT EXISTS songplays (songplay_id serial PRIMARY KEY, 
                                        start_time timestamp, 
                                        user_id int, 
                                        level varchar, 
                                        song_id varchar, 
                                        artist_id varchar, 
                                        session_id int, 
                                        location varchar, 
                                        user_agent varchar)
    ```
    > That is the fact table. That contains logs data of music playing application


* Users table: 
    ```sql=
    CREATE TABLE IF NOT EXISTS users (user_id int not null PRIMARY KEY, 
                                    first_name varchar, 
                                    last_name varchar, 
                                    gender varchar, 
                                    level varchar)
    ```
    > That is the dimension table. That contains user data of music playing application

* Songs table: 
    ```sql=
    CREATE TABLE IF NOT EXISTS songs (song_id varchar not null PRIMARY KEY, 
                                      title varchar, 
                                      artist_id varchar, 
                                      year int, 
                                      duration numeric)
    ```
    > That is the dimension table. That contains song data of music playing application

* Artists table: 
    ```sql=
    CREATE TABLE IF NOT EXISTS artists (artist_id varchar not null PRIMARY KEY, 
                                        name varchar, 
                                        location varchar, 
                                        latitude numeric, 
                                        longitude numeric)
    ```
    > That is the dimension table. That contains artists data of music playing application

* Time table: 
    ```sql=
    CREATE TABLE IF NOT EXISTS time (start_time timestamp PRIMARY KEY, 
                                    hour int, 
                                    day int, 
                                    week int, 
                                    month int, 
                                    year int, 
                                    weekday int)
    ```
    > That is the dimension table. That contains time data of logs data.



Statistics
---
* Number of songs: 71
* Number of artists: 69
* Number users: 96
* 2 artists have 2 songs in this database: Casual, Clp
* Just one song matched between songs and songplays: Setanta matins	(ID: SOZCTXZ12AB0182364)



## Appendix and FAQ

:::info
**Please assess my project?** Leave a comment!
:::

###### tags: `Udacity` `Data Modelling` `Postgres` `Pipeline`
