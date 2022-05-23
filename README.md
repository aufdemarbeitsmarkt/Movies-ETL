# Movies-ETL

## Overview 
An exercise in Extract, Transform, Load (ETL) processes utilizing datasets from Wikipedia and Kaggle. Our tools included python (namely pandas, numpy, and regex, among others) as well as PostgreSQL and pgAdmin. 

To support a company hackathon, we extracted movie-related data from Wikipedia and Kaggle data from their respective files, transformed the datasets by cleaning them up and joining them together, and loaded the cleaned dataset into a SQL database.

## Summary 

The ETL process was initially worked out in a piecemeal fashion in [transform.ipynb](transform.ipynb). Subsequently, the core pieces of of the ETL process were condensed into a set of functions, allowing this process to be repeated with ease as well as with other datasets. 

A brief description of each step of this iterative process is described below. 

### `ETL_function_test.ipynb` 

In [ETL_function_test.ipynb](ETL_function_test.ipynb), a function - `extract_transform_load()` - was created to return each dataset as a pandas DataFrame. 


### `ETL_clean_wiki_movies.ipynb`

[ETL_clean_wiki_movies.ipynb](ETL_clean_wiki_movies.ipynb) built on the previous notebook. Here, the aforementioned `extract_transform_load()` was expanded to include key clean-up tasks; Wikipedia does not have standardized representation of movie-related information, so this step was especially important. Additionally, the `clean_movie()` was called on each movie to ensure redundant column names were made uniform and alternate titles were logged in one column*. 

*note: later in the process, we drop alternate titles because we found an insignificant number of movies had this information; as a result, it was considered superfluous. That said, a future dataset may have more robust alternate title information and may be not be filtered out during the clean-up process. 


### `ETL_clean_kaggle_data.ipynb`

In [ETL_clean_kaggle_data.ipynb](ETL_clean_kaggle_data.ipynb), cleanup of our Kaggle datasets was added to the `extract_transform_load()`. Additionally, the  the Wikipedia and Kaggle datasets were merged. Lastly, the ratings data was aggregated then merged with the full movie DataFrame.


### `ETL_create_database.ipynb`

The final - Load - step of the ETL process can be found in [ETL_create_database.ipynb](ETL_create_database.ipynb). Here, a connection to a local SQL database was created with tables for `movies` and `ratings` created (the cleaned and merged Wikipedia and Kaggle datasets as well as the raw ratings data*, respectively.)

*note: due to size constraints, the ratings data is not included in this repo. However, this data can be downloaded [here](https://www.kaggle.com/datasets/rounakbanik/the-movies-dataset?select=ratings.csv). 