# Data Modeling with Postgres Project Starter Code

The objective of this project is to apply data modeling with Postgres and build an ETL pipeline using Python.

<!--more-->

[//]: # (Image References)

[image1]: ./images/relaciones.jpg "Database Schema for Sparkify"


---


#### How to run the program with your own code

Go to Desktop and open a terminal.

For the execution of your own code, we head to the Project Workspace.

To build the schema or to drop the tables and rebuild them. Once the database is created, this fils executes the SQL queries in sql_queries.py to build tables in the schema.
```bash
  python create_tables.py
```

To execute the ETL to load data into the tables.
```bash
  python etl.py
```

Implements the same script as etl.py, but on a single song file and log file.
```bash
  etl.ipynb
```

Some queries used to test the results of the ETL using:
```bash
  test.ipynb
```


---

The summary of the files and folders within repo is provided in the table below:

| File/Folder              | Definition                                                                                                   |
| :----------------------- | :----------------------------------------------------------------------------------------------------------- |
| data/*                   | Folder that contains all the json files with the data used in this project.                                  |
| images/*                 | Folder containing the images of the project.                                                                 |
|                          |                                                                                                              |
| test.ipynb               | Displays the first few rows of each table to let check the database.                                         |
| create_tables.py         | Drops and creates the tables. This file is to reset the tables before each time that run the ETL scripts.    |
| etl.ipynb                | Reads and processes a single file from song_data and log_data and loads the data into the tables. This notebook contains detailed instructions on the ETL process for each of the tables. |
| etl.py                   | Reads and processes files from song_data and log_data and loads them into the tables.                        |
| sql_queries.py           | Contains all the sql queries, and is imported into the last three files above.                               |
|                          |                                                                                                              |
| README.md                | Contains the project documentation.                                                                          |
| README.pdf               | Contains the project documentation in PDF format.                                                            |


---

**Steps to complete the project:**  

1. Define fact and dimension tables for a star schema for a particular analytic focus.
2. Write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.


## [Rubric Points](https://review.udacity.com/#!/rubrics/2500/view)
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
## Scenario.

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.


## Database Schema for Sparkify.

In our scenario, we have one dataset of songs where each file is in JSON format and contains metadata about a song and the artist of that song. The second dataset consists of log files in JSON format and simulates activity logs from a music streaming app (based on specified configurations).

Using the song and log datasets, the database schema looks like this:

![alt text][image1]
