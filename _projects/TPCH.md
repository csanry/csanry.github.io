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

In this project, I design an ELT pipeline using `Snowflake` as the cloud data warehouse. I define my transformation pipelines in a `dbt` project, and orchestrate the pipelines using `Airflow` and `Astronomer Cosmos`.

The decision to use `ETL` or `ELT` informs subsequent considerations about data pipeline architecture and implementation. 

This project showcases the `ELT` approach, which has grown in popularity with the advent of [massively parallel processing databases]{:target="_blank"} and cloud infrastructure.

The crux of the ELT process is to load the data directly into your data warehouse, as opposed to maintaining a dedicated server responsible for processing and transforming your data.

<figure>
  <img src="{{site.url}}/assets/img/TPCH/etl_vs_elt.png" width="100%" height="auto" />
  <figcaption>Visualisation of the difference in ETL and ELT</figcaption>
</figure>

This key difference is ELT's most compelling case - when data is loaded with minimal processing into the data warehouse, its raw state is retained, meaning that downstream pipelines can be recreated, rewritten, or dropped easily in response to changing business priorities.

When used in conjunction with tools like `dbt`, ELT shifts the responsibility of developing data pipelines to `Analytics Engineers / Data Analysts`, individuals who understand the business better than Data Engineers, but might not have the technical chops to write scalable, robust ETL code.


## 📊 Tools primer

`Snowflake` is a cloud data platform, which is a key component of the [modern data stack]{:target="_blank"}. It supports transformation workloads written in SQL, along with a suite of other nifty features, such as autoscaling, a RESTful API, and extension to a broad ecosystem of 3rd party tools and technologies.

`Airflow` is an open source workflow management tool to orchestrate data engineering pipelines. To allow better visibility into the lineage of tasks, this project uses [Astronomer Cosmos]{:target="_blank"} to integrate `dbt` and `Airflow`.


## 🖥️ TPC-H Data

The [TPC-H benchmark]{:target="_blank"} is a widely recognised tool for evaluating the performance of data processing systems. It consists of a suite of decision support queries based on a multi-table schema.

I chose to build the project on the `TPC-H` dataset due to the following reasons:

`Realism:` `TPC-H` simulates real-world business operations, entities, and relationships

`Integration with Snowflake:` `TPC-H` data tables are available as sample data within Snowflake

`Size:` Because of the size, building data pipelines from the `TPC-H` data requires efficiency in data processing and transformation jobs

<figure>
  <img src="{{site.url}}/assets/img/TPCH/tpch_schema.png" width="70%" height="auto" />
  <figcaption>Schema of the TPC-H dataset</figcaption>
</figure>

## 🖥️ Process 

<figure>
  <img src="{{site.url}}/assets/img/TPCH/airflow-demo-3.gif" width="100%" height="auto" />
  <figcaption>Spinning up a local instance of the project</figcaption>
</figure>

<!-- 
In my humble opinion, there are two big pros with ELT: greater flexibility and better experience. ELT eliminates the need for a dedicated staging environment - when data is loaded with minimal processing into the data warehouse, its raw state is retained, meaning that downstream pipelines can be recreated, rewritten, or dropped easily in response to changing business priorities. Secondly, ELT democratises the responsibility of developing data pipelines. With dbt, transformation pipelines can be written by Analytics Engineers / Data Analysts, individuals who might understand the business better than Data Engineers, but might not have the technical chops to write scalable, robust ETL code.

Extract:

The Extract phase is responsible for pulling raw data from source systems. In the case of TPC-H, this could involve generating or importing the dataset (such as customer orders, suppliers, line items, etc.) into a staging area.
Data may come from various sources such as transactional databases, external APIs, or files.
Load:

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

Fast: Colima uses a lightweight VM (via qemu or HyperKit) to run containers and can be faster than traditional Docker Desktop on macOS. -->

<!-- **Key point to highlight**

<figure>
  <img src="{{site.url}}/assets/img/TPCH/airflow-demo-2.gif" width="100%" height="auto" />
  <figcaption>Users can examine trends in employment rates and salaries for specific universities and degrees</figcaption>
</figure>


**Key point to highlight**

Writeup -->



[Explore the project here]{:target="_blank"}
{:.read-more}

<br>

**_Further Reading_**

\[1\] A brief introduction to Airflow internals / architecture can be found [here](https://medium.com/apache-airflow/airflow-architecture-simplified-3d582fc3ccb0){:target="_blank"}

\[2\] A more detailed comparison of ETL vs ELT can be found [here](https://rivery.io/blog/etl-vs-elt){:target="_blank"}


<!-- Links -->
[TPC-H benchmark]: https://docs.snowflake.com/en/user-guide/sample-data-tpch
[modern data stack]: https://www.thoughtspot.com/data-trends/best-practices/modern-data-stack
[Explore the project here]: https://github.com/csanry/dbt-tpch-pipeline
[massively parallel processing databases]: https://airbyte.com/data-engineering-resources/mpp-database
[Astronomer Cosmos]: https://www.astronomer.io/cosmos