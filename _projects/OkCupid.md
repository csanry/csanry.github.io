---
layout: project
title: OkCupid Dashboard 
date: 10 March 2024
image: /assets/img/OkCupid/featured_image_cupid.png
links:
  - title: Dashboard link
    url: https://public.tableau.com/app/profile/clarence/viz/Cupidsworkstation/main
    target: _blank
description: >
  Finding love through data
hide_description: true
---

1. TOC
{:toc}

## 🚩 Goal 

Understand the demographics and lifestyles of users on OkCupid [(view on kaggle here)]{:target="_blank"}


## 📊 Data

This dashboard ingests data gathered from [OkCupid]{:target="_blank"} profiles from 2012.
Numerical columns were cleaned and grouped into bins to better understand their distribution. Histograms were subsequently generated to visualise these distributions.
The original dataset contained several fields which numerous categories. To faciliate visualisation, low frequency categories were combined to present the data in a clearer manner. 


## 🖥️ Dashboard

<figure>
  <img src="{{site.url}}/assets/img/OkCupid/dashboard_overview.png" width="100%" height="auto" />
  <figcaption>High level overview of the dashboard</figcaption>
</figure>

## 🔥 Features

**The dashboard allows the user to explore the data in the following manner** <br>
1. Select some basic information about the user, such as their `gender` and `sexual orientation`
2. Select user preferences, such as desired `ethnicity`, `education`, and `profession`
3. View individual profiles and how they stack up against other users in the curated dataset

<figure>
  <img src="/assets/img/OkCupid/view_one.gif" alt="" width="100%" height="auto" />
  <figcaption>The user is prompted to select their characteristics and desired traits to filter out profiles which are not good matches</figcaption>
</figure>

The Tableau dashboards used in this project are dynamic and designed to facilitate exploration of the data in an intuitive manner. In addition to using the filtering options on the left of the dashboard, the user is also able to interactive define their preferences by selecting their desired traits from the treemaps and barcharts in the dashboard

<figure>
  <img src="/assets/img/OkCupid/view_two.gif" alt="" width="100%" height="auto" />
  <figcaption>Each visualisation is a dynamic filter to allow the user to drill down by specific characteristics</figcaption>
</figure>


The final view allows the user to view individual profiles from the reduced dataset. 

<figure>
  <img src="/assets/img/OkCupid/view_three.gif" alt="" width="100%" height="auto" />
  <figcaption>Users can filter from a selection of metrics to examine correlations. Hovering over a data point reveals additional information.</figcaption>
</figure>


[Play around with the dashboard here]{:target="_blank"}
{:.read-more}

<br>

**_Further Reading_**

\[1\] A primer about the science of attraction can be found [in this video](https://www.ted.com/talks/dawn_maslar_the_science_of_attraction?language=en){:target="_blank"}


<!-- Links  -->
[(view on kaggle here)]: https://www.kaggle.com/datasets/yashsrivastava51213/okcupid-profiles-dataset
[OkCupid]: https://www.okcupid.com/
[Play around with the dashboard here]: https://public.tableau.com/app/profile/clarence/viz/Cupidsworkstation/main