# AWS EMR Spark Data Analysis

This repository, `aws-emr-spark`, showcases robust **Python** and **data analysis skills** by leveraging **Apache Spark** on **AWS Elastic MapReduce (EMR)**. It provides a practical example of processing and analyzing large datasets, specifically the IMDB dataset, to extract meaningful insights.

## Project Overview

This project demonstrates how to perform data analysis on a large dataset using **PySpark** on an **AWS EMR cluster**. The analysis focuses on a subset of IMDB's data, including information about actors, genres, movie principals, and movie ratings.

The notebook walks through the following key steps:

* **Setup and Installation**: Installing necessary Python packages (`pandas`, `matplotlib`) on the EMR cluster.
* **Data Loading**: Efficiently loading large `.tsv` datasets from **Amazon S3** into **Spark DataFrames**.
* **Data Inspection**: Displaying schemas, sample data, and row/column counts for each DataFrame.
* **Data Transformation**: Performing operations like dropping columns, filtering, and denormalizing data (e.g., exploding genres).
* **Data Analysis - Movie Genres**:
    * Identifying unique movie genres.
    * Calculating the average rating for each genre.
    * Visualizing genre ratings using horizontal bar charts.
* **Data Analysis - Job Categories**:
    * Identifying unique job categories.
    * Counting the number of titles associated with each job category.
    * Visualizing the top job categories using bar charts.

## Sample Analysis & Capabilities

Here are some key outputs and insights:

### Data Loading and Initial Inspection

Data from S3 is loaded into Spark DataFrames. For instance, the `name` DataFrame, containing information about actors, looks like this:

```
root
 |-- nconst: string (nullable = true)
 |-- primaryName: string (nullable = true)
 |-- birthYear: string (nullable = true)
 |-- deathYear: string (nullable = true)
 |-- primaryProfession: string (nullable = true)
 |-- knownForTitles: string (nullable = true)

+---------+---------------+---------+---------+-----------------------------------+---------------------------------------+
|nconst   |primaryName    |birthYear|deathYear|primaryProfession                  |knownForTitles                         |
+---------+---------------+---------+---------+-----------------------------------+---------------------------------------+
|nm0000001|Fred Astaire   |1899     |1987     |soundtrack,actor,miscellaneous     |tt0027125,tt0050419,tt0053137,tt0072308|
|nm0000002|Lauren Bacall  |1924     |2014     |actress,soundtrack                 |tt0075213,tt0117057,tt0038355,tt0037382|
|nm0000003|Brigitte Bardot|1934     |\N       |actress,soundtrack,music_department|tt0049189,tt0054452,tt0056404,tt0057345|
+---------+---------------+---------+---------+-----------------------------------+---------------------------------------+
only showing top 3 rows

13329316
```

### Analyzing Movie Genres

The project denormalizes movie genres and calculates the average rating per genre:

```
+-----------------------------------+
|total number of unique movie genres|
+-----------------------------------+
|                                 29|
+-----------------------------------+
```

```
+-------------------+
|unique movie genres|
+-------------------+
|Mystery            |
|Musical            |
|Sport              |
|Action             |
|Talk-Show          |
|Romance            |
|Thriller           |
|Reality-TV         |
|Family             |
|Fantasy            |
|History            |
|Animation          |
|Film-Noir          |
|Short              |
|Sci-Fi             |
|News               |
|Drama              |
|Documentary        |
|Western            |
|Comedy             |
|Crime              |
|War                |
|Game-Show          |
|Adult              |
|Music              |
|Biography          |
|Adventure          |
|Horror             |
+-------------------+
```

Average ratings per genre:

```
+-----------+-------------+
|genres     |averageRating|
+-----------+-------------+
|Mystery    |5.847        |
|Musical    |6.187        |
|Action     |5.732        |
|Sport      |6.623        |
|Talk-Show  |6.858        |
|Romance    |6.102        |
|Thriller   |5.613        |
|Reality-TV |6.701        |
|Family     |6.205        |
|Fantasy    |5.898        |
|History    |6.798        |
|Animation  |6.367        |
|Film-Noir  |6.463        |
|Sci-Fi     |5.353        |
|News       |7.203        |
|Drama      |6.248        |
|Documentary|7.216        |
|Western    |5.84         |
|Comedy     |5.906        |
|Crime      |5.985        |
+-----------+-------------+
```

### Analyzing Job Categories

The repository also analyzes job categories associated with titles:

```
total number of unique job categories: 12
```

```
+-------------------+
|category           |
+-------------------+
|actress            |
|producer           |
|production_designer|
|writer             |
|actor              |
|cinematographer    |
|archive_sound      |
|archive_footage    |
|self               |
|editor             |
|composer           |
|director           |
+-------------------+
```

Top job categories by count:

```
+-------------------+--------+
|category           |count   |
+-------------------+--------+
|actor              |13443688|
|self               |10562296|
|actress            |10492210|
|writer             |8495903 |
|director           |7006843 |
|producer           |3944711 |
|cinematographer    |2068164 |
|composer           |2014049 |
|editor             |2012800 |
|archive_footage    |404581  |
|production_designer|383761  |
|archive_sound      |4794    |
+-------------------+--------+
```

## Getting Started

To replicate this analysis, you will need:

* An **AWS account** with permissions to create and manage EMR clusters and S3 buckets.
* The IMDB dataset (or a similar large, tab-separated dataset) uploaded to an **S3 bucket**.
* Familiarity with **PySpark** and **Jupyter notebooks**.

## Usage

1.  **Launch an EMR Cluster**: Configure an EMR cluster with Spark installed.
2.  **Upload Data**: Ensure your IMDB `.tsv` files are accessible from an S3 bucket.
3.  **Run the Notebook**: Execute the provided Jupyter notebook (or adapt the Spark code) on the EMR cluster. The notebook demonstrates the full data loading, transformation, and analysis workflow.

## Contributing

Feel free to fork this repository, suggest improvements, or open issues. Contributions that enhance the analysis, optimize Spark jobs, or add new functionalities are highly welcome!
