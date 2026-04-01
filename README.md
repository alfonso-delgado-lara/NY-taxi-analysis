# NYC Taxi Analysis with Apache Spark

## Overview
This project analyzes large-scale New York City taxi trip data using **Apache Spark**, combining three different processing paradigms:

- **RDDs**
- **Spark DataFrames**
- **Spark SQL**

The goal is not only to extract useful insights from real-world mobility and financial data, but also to compare how different Spark abstractions behave when solving the same analytical problem at scale.

The project focuses on four main questions:

1. **How does average taxi speed vary throughout the day?**
2. **What are the most frequent taxi routes in NYC?**
3. **Which routes generate the highest average card tips?**
4. **At what hours is driving most profitable in terms of income per minute?**

---

## Objectives
This work was designed to combine:

- **distributed data processing**
- **performance-oriented computing**
- **real-world business-oriented analysis**
- **comparison of multiple Spark workflows**

In other words, the project is both **technical** and **analytical**: it studies the data itself while also evaluating the computational tools used to process it.

---

## Dataset
The analysis uses **NYC taxi trip data** stored in **Parquet** format, together with the `taxi_zone_lookup.csv` file to map pickup and dropoff location IDs to actual NYC boroughs and zones.

The raw trip data includes variables such as:

- pickup and dropoff timestamps
- trip distance
- pickup and dropoff location IDs
- tip amount
- fare-related variables

---

## Tech Stack
- **Python**
- **Apache Spark / PySpark**
- **RDDs**
- **Spark DataFrames**
- **Spark SQL**
- **Pandas**
- **Matplotlib**

---

## Project Structure
The notebook is organized into several analytical sections.

### 1. Average taxi speed by hour
This section estimates the **average speed of taxi rides for each hour of the day**.

To make the calculation robust:

- pickup and dropoff timestamps are converted into **UNIX timestamps**
- trip duration is computed in seconds and then hours
- speed is expressed in **km/h**
- unrealistic records are filtered out:
  - zero-distance trips
  - trips with identical pickup/dropoff times
  - trips shorter than 30 seconds
  - speeds above a realistic threshold

The same task is then solved using:

- **RDDs**
- **Spark DataFrames**
- **Spark SQL**

This allows a direct comparison between the three approaches, both in terms of logic and execution time.

#### Key insight
The results clearly show a strong daily traffic pattern:
- the **highest average speeds** occur early in the morning
- the **lowest speeds** appear during the busiest daytime and afternoon hours

This reflects the impact of congestion on urban mobility.

---

### 2. Performance comparison across Spark paradigms
One of the strongest parts of the project is that it does not stop at obtaining the result: it also compares **how efficiently** the same analysis can be solved.

For the hourly speed task, the three approaches are benchmarked:

- **RDDs**
- **DataFrames**
- **Spark SQL**

The results show that:

- **RDDs** are the slowest approach
- **DataFrames** improve performance significantly
- **Spark SQL** achieves the best execution time in this task

This makes the notebook especially valuable from a portfolio perspective, because it demonstrates not only data analysis skills, but also a practical understanding of **computational efficiency in distributed systems**.

---

### 3. Most frequent taxi trips
This section identifies the **most common pickup-dropoff route pairs** in NYC.

The workflow includes:

- selecting pickup and dropoff location IDs
- counting route frequencies with Spark
- sorting the results in descending order
- joining the route IDs with `taxi_zone_lookup.csv` for interpretability

This transforms raw numeric route pairs into real geographic information, making the results much more meaningful.

#### Why this matters
This analysis shows how to move from low-level event data to **mobility patterns** that could be useful for:
- transportation planning
- demand concentration analysis
- operational optimization

---

### 4. Economic analysis: average card tips by route
This section studies **tipping behavior** across routes.

The analysis:

- filters invalid trips
- removes null `tip_amount` values
- groups trips by pickup-dropoff route
- computes the **average card tip amount** per route
- ranks the top routes by average tipping

The final output is visualized to highlight which routes are associated with higher tipping behavior.

#### Why this matters
This is a good example of how trip-level data can be used to generate **financial and behavioral insights**, not just mobility metrics.

---

### 5. Economic analysis: income per minute by hour
The final section explores **profitability by time of day**.

For each trip, the notebook computes:

- trip duration in minutes
- income per minute
- pickup hour

It then aggregates the data by hour to estimate:

- number of trips
- average income per minute
- average income per trip
- average trip duration

#### Key insight
This analysis goes beyond demand or speed alone and asks a more operational question:

> **When is it most profitable to drive?**

That makes it especially relevant from a business perspective, since it combines temporal patterns with revenue efficiency.

---

## Main Strengths of the Project
What makes this project strong is the combination of several dimensions:

### Technical strengths
- Uses **Apache Spark** on a real large-scale dataset
- Works with **RDDs, DataFrames and SQL**
- Includes **performance benchmarking**
- Applies realistic data-cleaning criteria
- Handles time-based feature engineering

### Analytical strengths
- Connects mobility data with business questions
- Produces interpretable visualizations
- Studies both **traffic behavior** and **economic outcomes**
- Enriches raw IDs with real zone information

### Portfolio strengths
This project complements more standard ML projects very well because it shows:
- distributed processing skills
- big data handling
- performance awareness
- real analytical storytelling

---

## Key Takeaways
From a portfolio perspective, this project demonstrates that I can:

- process and analyze large datasets with **Spark**
- choose between different distributed abstractions depending on the problem
- perform **data cleaning, transformation and aggregation** at scale
- compare computational approaches, not just produce results
- extract business insights from operational data

---

## Possible Extensions
Some natural next steps for this project would be:

- adding geospatial visualizations of the most frequent routes
- building predictive models for trip duration or tip amount
- studying seasonality or weekday/weekend patterns
- deploying summary dashboards with Streamlit
- running the same workflow on a cluster setup instead of local execution

---

## Authors
- Alfonso Delgado Lara
- Diego Rivera Suárez
- María Pérez García
- Sara Freire Rotella
