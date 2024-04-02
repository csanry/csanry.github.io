---
layout: project
title: Graduate Employment Survey Dashboard 
date: 18 August 2023 
image: /assets/img/GES/featured_image_ges.png
links:
  - title: Dashboard link
    url: https://public.tableau.com/app/profile/clarence/viz/GESInsights/GESDashboard
    target: _blank
description: >
  Identifying graduate employment outcomes and trends from the GES from 2013 - 2021
hide_description: true
---

1. TOC
{:toc}

[`data analysis`]() [`data visualisation`]()

## 🚩 Goal

> The Graduate Employment Survey is a yearly initiative by Singapore's 6 autonomous universities to assess employment outcomes from their graduating cohorts.

This dashboard aims to utilise the responses collected from the **Graduate Employment Survey** to understand:
1. How overall employment rates vary across universities, degrees, and years
2. Trends in salaries by universities, degrees, and years


## 📊 Data

Data from the Graduate Employment Survey from the years 2013 - 2021 was retrieved from [data.gov.sg]{:target="_blank"}, a public API repository of datasets related to Singapore.

The survey is jointly conducted by **NTU, NUS, SMU, SIT (from 2014), SUTD (from 2015) and SUSS (from 2018)** annually to survey the employment conditions of graduates about six months after their final examinations. As a result, data points for SUTD and SUSS will not be available in the initial years. 


More information about the dataset and the download link can be [accessed here]{:target="_blank"}


## 🖥️ Dashboard 

<figure>
  <img src="{{site.url}}/assets/img/GES/dashboard_overview.png" width="100%" height="auto" />
  <figcaption>High level overview of the dashboard</figcaption>
</figure>


## 🔥 Features

**This dashboard aims to provide the user with a holistic view of key salary and employment trends**

The views on the left half show the 75th, 50th and 25th percentile of gross salaries by university.

<figure>
  <img src="{{site.url}}/assets/img/GES/view_one.gif" width="100%" height="auto" />
  <figcaption>Users can examine trends in employment rates and salaries for specific universities and degrees</figcaption>
</figure>


**Dynamic charts**

To better understand the employability trends of different degrees, users are able to use the filter options on the left section of the dashboard to select a subset of the data.

<figure>
  <img src="{{site.url}}/assets/img/GES/view_two.gif" width="100%" height="auto" />
  <figcaption>Users can filter and drill down the data using either the filter options on the left, or by using the dynamic charts</figcaption>
</figure>

**Yearly trends to identify changes over time**

Salary and employment rate percentages are colour coded by value so that the user is able to quickly identify the universities and degrees with the largest changes in these key metrics over the years.

<figure>
  <img src="{{site.url}}/assets/img/GES/view_three.gif" width="100%" height="auto" />
  <figcaption>The trend section of the dashboard provides average salaries across years for each university</figcaption>
</figure>


[Play around with the dashboard here]{:target="_blank"}
{:.read-more}

<br>

**_Further Reading_**

\[1\] More information about the 6 autonomous universities can be found [here](https://www.moe.gov.sg/post-secondary/overview/autonomous-universities/){:target="_blank"}


<!-- Links -->
[data.gov.sg]: https://beta.data.gov.sg/
[accessed here]: https://beta.data.gov.sg/datasets/d_3c55210de27fcccda2ed0c63fdd2b352/view
[Play around with the dashboard here]: https://public.tableau.com/app/profile/clarence/viz/GESInsights/GESDashboard