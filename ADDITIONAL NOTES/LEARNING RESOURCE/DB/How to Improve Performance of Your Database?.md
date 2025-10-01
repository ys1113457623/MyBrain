---
tags:
  - "#DailyNote"
created: 2025-05-18
review: 2025-05-18
---

# 🧠 How to Improve Performance of Your Database?

## 📅 Date:  
**Sunday, May 18th 2025**  


## Q) How to optimize the databases 

## Indexing

Indexes speed up data retrieval by creating pointers to rows, similar to a book’s index. Instead of scanning an entire table to find  specifics rows the database can use an index to locate the data quickly 

### Indexes Tradeoff
Indexes speed up read queries but slow down write operations because the index must also be updated during writes. They also consume disk space. 

## Materialized Views 

Materialized views store the pre computed result of a query. For complex queries involving joins or aggregations that run frequently computing the result once and storing it can reduce query time. For example, an analytics dashboard displays daily total sales aggregated by product category. This query involves joining orders, order_items, and products tables and performing aggregations. Creating a materialized view, daily_sales_by_category, that stores these daily totals allows the dashboard to load much faster by querying this simple view.

### Tradeoff
The data in a Materialized view can become stale. It needs a refresh strategy that consumes resources. 
![[Pasted image 20250518175603.png]]

## Denormalizations
Normalization is organizing database tables to reduce data redundancy and improve data integrity, often involving splitting data into multiple related tables. Denormalization is the opposite process: intentionally adding redundant data to one or more tables to avoid costly joins when querying. For example, an e-commerce application must frequently display the product name and order details. A normalized design might require joining the orders table with the products table. To speed this up, you could denormalize by adding a product_name column directly to the orders table. This avoids the join during reads.

**Analogy:**
Imagine a delivery log that includes not just the order ID, but also the customer’s name and address, even though it’s stored elsewhere. That way, you don’t need to look up customer info every time—it’s already there.

**Tradeoff**
- Good: Fewer joins = faster reads.
- Bad: If that customer changes their address, you now have to update it in multiple places = risk of inconsistency.

  

- Good: Fewer joins = faster reads.
- Bad: If that customer changes their address, you now have to update it in multiple places = risk of inconsistency.