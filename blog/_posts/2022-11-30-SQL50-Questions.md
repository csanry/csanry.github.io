---
layout: post
title: SQL50 - A High Level Introduction
image: /assets/img/2022-11-30-SQL50-Questions/featured_image.png
description: >
  Encapsulating my key takeaways from the neverending grind
hide_description: true 
hide_last_modified: true
sitemap: false
---

1. TOC
{:toc}

## What is SQL50?

SQL50 is a comprehensive set of [50 carefully curated problems by leetcode], designed to take the user through the key features of SQL. These questions cover a wide range of topics, from basic SQL syntax to complex queries and database design principles. 

The goal of SQL50 is to provide a structured approach to learning SQL, making it easier for beginners to get started and for experienced developers to refresh their knowledge. Each question is accompanied by a detailed explanation and example, ensuring that you not only know how to write the correct SQL query, but also understand why it works.

In this first part of a series of posts, I detail my key notes and pointers from going through SQL50 (**_why?_** Read on more about the importance of spaced repetition [below](#the-importance-of-spaced-repetition)).

While I attempt to solve the problems using the MySQL dialect, as that is the style that I am most familiar with, but many of the problems can be extended to other dialects - the key is to retain the core principles, so that you can adapt them to your specific needs.


## The Importance of Spaced Repetition

<figure>
  <img src="{{site.url}}/assets/img/2022-11-30-SQL50-Questions/spaced_repetition.png" width="100%" height="auto" />
  <figcaption>What is the best way to learn? Science says in short, frequent bursts at the start</figcaption>
</figure>

A short aside: when learning SQL, or any other skill for that matter, it's not enough to review the concepts once. To truly master them, you need to review and practice the concepts over time. This is the principle of spaced repetition.

The core tenet of spaced repetition is reviewing. When first learning about a subject, commit to reviewing the material at regular intervals. At the initial stage of the learning process, space the review intervals closely together, before gradually increasing the time between reviews. Revisiting key concepts and queries reinforces your memory of them, so that they come more naturally when you need it. Each review will also help to retain the information into your long term memory, making it easier to remember the information in the future. This is particularly useful for complex topics like joins, subqueries, and stored procedures, which can be difficult to grasp in one sitting.

Moreover, spaced repetition can help you identify areas where you're struggling, allowing you to organise your study efforts more intentionally. By regularly reviewing and practicing SQL, you can ensure that you're making steady progress and retaining the knowledge you've gained.

Remember, learning is not a sprint, but a marathon. With spaced repetition, you can make this activity more efficient and effective, and maybe better enjoy the experience along the way.


## Overview

SQL50 is structured into five main sections, each containing ten questions. The sections are designed to gradually increase in difficulty, starting with basic SQL commands and progressing to more complex topics.

The format of each question is consistent throughout the guide. Each question is presented in a clear, concise manner, followed by an example SQL query that demonstrates the concept being discussed. The solution to each question is then explained in detail, providing a thorough understanding of how the query works and why it is the correct solution.

## SELECT statements

In the next sections, we will start with the basics of SQL and gradually move towards more advanced topics.
The first few problems are important to get a solid understanding of how SQL queries are structured:

**Recyclable and Low Fat Products**

Write a solution to find the ids of products that are both low fat and recyclable. Return the result table in any order.

```sql
SELECT product_id
FROM products
WHERE low_fats = "Y" 
  AND recyclable = "Y"
```

**Find Customer Referee**

Find the names of the customer that are not referred by the customer with `id = 2`. Return the result table in any order.

```sql
SELECT name
FROM Customer
WHERE IFNULL(referee_id, 0) != 2
```

**Big Countries**

Write a solution to find the name, population, and area of the big countries. A country is big if it has an area of an least 3 million or it has a population of at least 25 million. Return the result table in any order.

```sql
SELECT
  name,
  population,
  area
FROM World
WHERE area >= 3000000
   OR population >= 25000000
```

**Article Views I**

Write a solution to find all the authors that viewed at least one of their own articles. Return the result table sorted by `id` in ascending order.

```sql
SELECT DISTINCT
  author_id AS id
FROM Views
WHERE author_id = viewer_id
ORDER BY id
```

**Invalid Tweets**

Write a solution to find the IDs of the invalid tweets. The tweet is invalid if the number of characters used in the content of the tweet is strictly greater than `15`. Return the result table in any order.

```sql
SELECT
  tweet_id
FROM Tweets
WHERE CHAR_LENGTH(content) > 15
```

**_Further Reading_**

\[1\] To try out SQL50 yourself, check out the [study guide] on leetcode

<br>
## Read more [posts](/blog/)
{:.read-more .no_toc}

<!-- Links  -->
[50 carefully curated problems by leetcode]: https://leetcode.com/studyplan/top-sql-50/ 
[study guide]: https://leetcode.com/studyplan/top-sql-50/