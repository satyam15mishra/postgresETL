# ETL Pipeline of Sparkifydb using Postgresql

## Purpose
The problem statement is related to a music streaming app called Sparkifydb wherein they want to use the existing data in json format to execute certain queries and possibly analysis. Hence, the requirement is to create an ETL pipeline in Postgresql using python (psycopg2).

## Database Schema Design
The database architecture used in this project is a star schema. In this architecture, the songplays table is acting as the fact table and others corresponding tables are dimension tables. Since there were multiple tables in the database and star schema is very efficient considering its easy readability and less complexity when it comes to running queries. Also, there is no point in making the architecture complicated by snowflake schema since the requirements can be satisfied using handful of queries and tables.

## Pipeline for ETL
+ The whole ETL is being executed using the script etl.py. This python script has distributed the whole task in three parts.
+ The first part is initializing the connection to database via psycopg2.
+ The second part is to insert data extracted via song files (song table and artist table) in json format to postgresql database.
+ The third part is to insert data extracted via log files (time table, user table and songplays table) in json format to postgresql database.
+ Finally, we end the cursor connection.
PS: sql_queries.py has all the sql queries, test.ipynb can be used to test if the database queries are working and create_tables.py is used to create tables via sql_queries.py.

## ERD for the Project
![ERD for Sparkify DB](/sparkifydb_erd.png "Entity Relationship Diagram")

## Project Repository Files
 + sql_queries.py: This python script contains all the sql queries (insert, create, and drop) which need to be executed.
 + etl.py: This python script is responsible for the ETL operations since it has functions which perform operations and initialize the database connection. It contains the ETL pipeline.
 + etl.ipynb: This python notebook does the same work as etl.py, its just that it is used to test different functions at any given instant. Also, it is efficient to use python script instead of this notebook if we need automation.
 + create_tables.py: This python script uses the queries in sql_queries.py in order to drop and create tables in the database.
 + test.ipynb: This python notebook is used to test whether our files are running, and if they are successfully inserting data into our schema.
 + generate_erd.py: This is simply used to get the ERD diagram for the model.

## How to Run the Project
To run the project, you need to run create_tables.py first in order to start the ETL pipeline. Post that, just execute etl.py and test.ipynb if you want to test the database.