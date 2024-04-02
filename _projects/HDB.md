---
layout: project
title: HDB Dashboard
date: 05 October 2023
image: /assets/img/HDB/featured_image_hdb.png
links:
  - title: Dashboard link
    url: https://public.tableau.com/app/profile/clarence/viz/SingaporeHDBResaleTransactions-Dashboard/HDBDashboard
    target: _blank
description: >
  Examining changes in HDB prices over time 
hide_description: true
---

1. TOC
{:toc}

[`data analysis`]() [`data visualisation`]()

## 🚩 Goal

> Buying (or at least, trying to buy) a flat built by the **Housing Development Board (HDB)** is a common headache faced by many Singaporeans. 

As choosing a HDB flat is a major financial decision for many, it is crucical to understand the trends and factors that influence HDB valuations to make as informed of a choice as possible. 

This dashboard aims to serve as a comprehensive and intuitive tool to explore and analyse:
1. Trends in HDB prices and # of transactions from 2009 - 2019
2. Factors that significantly affect HDB prices


## 📊 Data

Data for resale transactions from 2009 - 2019 was retrieved from [data.gov.sg]{:target="_blank"}, a public API repository of datasets related to Singapore.

Each row represents a unique transaction and includes details such as the `transaction_date` (representing the year and month when the transaction took place), `flat_type` (the type and size of the flat sold), `town` (district where the flat is situated), and `resale_price` (the price at which the flat was sold).

For a more comprehensive understanding of the dataset and to access the download link, please refer to [this link]{:target="_blank"}.


## 🖥️ Dashboard

<figure>
  <img src="{{site.url}}/assets/img/HDB/dashboard_overview.png" width="100%" height="auto" />
  <figcaption>High level overview of the dashboard</figcaption>
</figure>


## 🔥 Features

**This dashboard is split into 2 main sections**
1. The left section focuses on the **number of transactions** over time 
2. The right section focuses on the **resale price of the flats**


**Global filters on flat types, year, and location**

To better understand trends in prices for different areas and flat types, users are able to use the filter options at the top section to select a subset of data.

<figure>
  <img src="{{site.url}}/assets/img/HDB/view_one.gif" width="100%" height="auto" />
  <figcaption>Users are able to filter transactions by certain flat characteristics</figcaption>
</figure>


**Visualising transactions by district over years**

The geographical map showing the breakdown of prices by district features an animation which allows the user to loop through and view changes in metrics over time. 

<figure>
  <img src="{{site.url}}/assets/img/HDB/view_two.gif" width="100%" height="auto" />
  <figcaption>The geographical map provides a playback option to view changes in price and transactions by district</figcaption>
</figure>


**Interactivity**

In addition to presenting 5 number summaries in the boxplots in the right region, users are also able to interact with the charts to either filter down the data, or to view individual transactions.

<figure>
  <img src="{{site.url}}/assets/img/HDB/view_three.gif" width="100%" height="auto" />
  <figcaption>Users are able to use the dynamic filters to narrow down their options</figcaption>
</figure>



[Play around with the dashboard here]{:target="_blank"}
{:.read-more}

<br>

**_Further Reading_**

\[1\] A brief history about the HDB scheme can be found [here](https://www.hdb.gov.sg/about-us/history/design-through-the-decades){:target="_blank"}

<!-- Links  -->
[data.gov.sg]: https://beta.data.gov.sg/
[this link]: https://beta.data.gov.sg/collections/189/datasets/d_ebc5ab87086db484f88045b47411ebc5/view
[Play around with the dashboard here]: https://public.tableau.com/app/profile/clarence/viz/SingaporeHDBResaleTransactions-Dashboard/HDBDashboard