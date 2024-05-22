---
layout: project
title: Data Engineering Project
date: 18 August 2023 
image: /assets/img/TPCH/featured_image_tpch.png
links:
  - title: Repository link
    url: https://github.com/csanry/dbt-tpch-pipeline
    target: _blank
description: >
  ELT pipeline built with dbt, snowflake and airflow
hide_description: true
---

1. TOC
{:toc}

[`data engineering`]()[`dbt`]()[`snowflake`]()

## 🚩 Goal

> This project involves the extraction and transformation of data from the TPC-H (Transaction Processing Performance Council - Benchmark H) dataset. This is done in dbt and snowflake, and orchestrated using airflow.

Deciding on an ETL vs ELT approach is critical when designing data pipelines. The traditional, time-tested ETL methodology first transforms data on a dedicated processing server, before ingesting said data into the data warehouse. With the advent of massively parallel processing databases and cloud infrastructure, ELT has emerged as an extremely viable alternative. Load the data directly into your data warehouse, which takes care of your staging, scaling and assigning processing / computation units to meet demand, and documentation. What's not to love? 

In my humble opinion, there are two big pros with ELT: greater flexibility and better experience. ELT eliminates the need for a dedicated staging environment - when data is loaded with minimal processing into the data warehouse, its raw state is retained, meaning that downstream pipelines can be recreated, rewritten, or dropped easily in response to changing business priorities. Secondly, ELT democratises the responsibility of developing data pipelines. With dbt, transformation pipelines can be written by Analytics Engineers / Data Analysts, individuals who might understand the business better than Data Engineers, but might not have the technical chops to write scalable, robust ETL code.

In this project, I design an ELT pipeline using snowflake as the cloud data warehouse of choice. Transformation pipelines are defined in a dbt project, and the whole shebang is orchestrated using airflow + astro cosmos. 

I touch on some pains in setting up and managing airflow. 



## 📊 Tools primer

Snowflake is purpose-built for modern data workloads, providing several advantages over traditional on-premises and other cloud solutions:

Separation of Storage and Compute: Snowflake’s architecture separates storage from compute, allowing for independent scaling. This makes it particularly useful for handling large datasets and performing complex transformations without compromising performance.

Fully Managed Service: Snowflake handles infrastructure management, scalability, and data security, allowing data engineers and analysts to focus more on data workflows and analytics rather than on maintaining the platform itself.

Zero-Copy Cloning: Snowflake’s ability to clone databases without actually duplicating the data enables efficient testing and iteration of your data pipeline without the overhead of traditional data duplication.

Data Sharing and Collaboration: Snowflake provides seamless data sharing across different teams and organizations, enhancing collaboration.

SQL-Based Transformation: Snowflake supports SQL-based transformations, which are familiar to most data engineers, analysts, and data scientists, minimizing the learning curve.

Support for Structured and Semi-Structured Data: Snowflake can handle not only structured data but also semi-structured data (JSON, XML, Parquet, etc.), making it highly flexible for modern data needs.

## 🖥️ TPC-H Data

The TPC-H benchmark is a widely recognized tool for evaluating the performance and scalability of data processing systems. It consists of a set of decision support queries based on a multi-table schema representing the data of a typical business’s operations. Using TPC-H data for an ELT pipeline in Snowflake offers several advantages:

Realistic and Industry-Standard Dataset: TPC-H simulates real-world business operations, and its use allows teams to focus on solving practical, business-relevant problems.

Complex Data Transformations: TPC-H queries are designed to test complex joins, aggregations, and other data manipulation operations. This gives teams a chance to fine-tune performance and test the scalability of the ELT pipeline with challenging data workloads.

Performance Benchmarking: Implementing TPC-H in your ELT pipeline allows you to benchmark the performance of your data processing and transformation jobs, ensuring that your pipeline can handle enterprise-scale data volumes efficiently.

Consistency: TPC-H provides a consistent set of queries and datasets for comparing different solutions, making it an excellent choice for testing and optimizing Snowflake’s capabilities in the context of data transformation.

## 🖥️ Process 

<figure>
  <img src="{{site.url}}/assets/img/TPCH/featured_image_tpch.png" width="100%" height="auto" />
  <figcaption>Fig caption</figcaption>
</figure>

Extract:

The Extract phase is responsible for pulling raw data from source systems. In the case of TPC-H, this could involve generating or importing the dataset (such as customer orders, suppliers, line items, etc.) into a staging area.
Data may come from various sources such as transactional databases, external APIs, or files.
Load:

Once data is extracted, it is loaded into Snowflake. Snowflake’s COPY INTO command allows for fast, parallelized data loading from files stored in cloud storage (such as Amazon S3 or Google Cloud Storage).
Snowflake can efficiently handle massive datasets, so even large volumes of TPC-H data can be loaded quickly and accurately.
Transform:

The most critical phase of the pipeline is the Transform stage, where data is cleansed, aggregated, and shaped into a form that can be used for business analysis.
With TPC-H, this phase would involve running complex queries (such as joins, aggregations, subqueries, and window functions) to prepare the data for reporting or analytics.
The beauty of Snowflake is that transformations can be done using simple SQL queries, leveraging Snowflake's powerful computational resources to handle even the most demanding transformations.


```yml
models:
  pipeline:
  # Config indicated by + and applies to all files under folder
    staging:
      +materialized: view
      snowflake_warehouse: dbt_wh
    marts:
      +materialized: table
      snowflake_warehouse: dbt_wh
```

```yml
snowflake:
  outputs:
    dev:
      type: snowflake
      account: fs77924.europe-west4.gcp
      user: csanry
      role: dbt_role
      warehouse: dbt_wh
      database: dbt_db
      schema: dbt_schema
      ...
  target: dev
```


## 🔥 Features

Containerisation

Colima is a container runtime for macOS and Linux. It is based on containers and provides Docker-compatible capabilities, which makes it easier to run containers without the need for Docker Desktop (which can be resource-heavy).
Colima leverages the lightweight virtual machine framework, providing a fast and efficient container environment with seamless integration for macOS users.

Fast: Colima uses a lightweight VM (via qemu or HyperKit) to run containers and can be faster than traditional Docker Desktop on macOS.

**Key point to highlight**

<figure>
  <img src="{{site.url}}/assets/img/TPCH/airflow-demo-2.gif" width="100%" height="auto" />
  <figcaption>Users can examine trends in employment rates and salaries for specific universities and degrees</figcaption>
</figure>


**Key point to highlight**

Writeup

<figure>
  <img src="{{site.url}}/assets/img/TPCH/airflow-demo-3.gif" width="100%" height="auto" />
  <figcaption>Users can filter and drill down the data using either the filter options on the left, or by using the dynamic charts</figcaption>
</figure>

**Yearly trends to identify changes over time**

[Explore the project here]{:target="_blank"}
{:.read-more}

<br>

**_Further Reading_**

\[1\] More information about airflow [here](){:target="_blank"}


<!-- Links -->
[data.gov.sg]: https://beta.data.gov.sg/
[accessed here]: https://beta.data.gov.sg/datasets/d_3c55210de27fcccda2ed0c63fdd2b352/view
[Explore the project here]: https://github.com/csanry/dbt-tpch-pipeline