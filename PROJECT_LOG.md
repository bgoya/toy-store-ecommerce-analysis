# Project Log — Toy Store E-Commerce Analysis

This document records the development of the project, from the initial exploration of the dataset to the final analysis and conclusions. It is intended to document the decisions, challenges, findings, and lessons learned throughout the process.

---

## 1. Project Overview

### Motivation

I wanted to put my recently acquired SQL knowledge into practice through a project based on a realistic dataset rather than isolated exercises.

I chose the [**Toy Store E-Commerce Database** from Maven Analytics](https://mavenanalytics.io/data-playground/toy-store-e-commerce-database) because it contains multiple related tables covering website sessions, pageviews, orders, products, and refunds. This makes it suitable for practicing SQL in a context similar to an e-commerce data analysis problem.

### Initial Objective

The initial goal of the project is to analyze the performance of the e-commerce business using SQL, with a particular focus on:

* Website traffic and session trends
* Conversion rates
* Marketing channel performance
* Revenue and profitability
* Product performance
* Customer behavior

The project may evolve as I explore the dataset and identify new questions worth investigating.

### Tools

* MySQL
* PopSQL
* SQL
* Git / GitHub

---

## 2. Dataset Exploration

### Source

**Dataset:** [Toy Store E-Commerce Database](https://mavenanalytics.io/data-playground/toy-store-e-commerce-database)

**Source:** [Maven Analytics](https://mavenanalytics.io/)

The dataset contains six related tables:

* `website_sessions`
* `website_pageviews`
* `orders`
* `order_items`
* `order_item_refunds`
* `products`

### Initial observations

The dataset contains information at different levels of granularity.

* `website_sessions`: one row represents a website session.
* `website_pageviews`: one row represents a pageview within a session.
* `orders`: one row represents an order.
* `order_items`: one row represents an individual item within an order.
* `order_item_refunds`: one row represents a refund associated with an order item.
* `products`: one row represents a product.

This distinction will be important when joining tables and calculating metrics, since joining tables with different granularities can result in duplicated records and incorrect aggregations.

### Initial Data Model

The main relationships identified so far are:

```text
website_sessions
       │
       ├──────── website_pageviews
       │
       └──────── orders
                    │
                    └──── order_items
                              │
                              ├──── products
                              │
                              └──── order_item_refunds
```

The `user_id` field also connects sessions and orders to the same user, although the dataset does not contain a separate `users` table.

### Next Step

The next step is to inspect the actual CSV files and verify the structure of the data before creating the MySQL database.
