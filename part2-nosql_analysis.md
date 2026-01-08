# NoSQL Justification Report

## Section A: Limitations of RDBMS

Relational databases use fixed schemas, which makes them less suitable for
highly diverse and evolving product catalogs. In FlexiMart’s case, different
products can have very different attributes. For example, laptops may require
fields such as RAM, processor, and storage, while shoes require size, color,
and material. Representing all these attributes in a relational table would
either result in many NULL values or require creating multiple specialized
tables, increasing complexity.

Frequent schema changes are another limitation of relational databases.
Whenever a new product type with new attributes is introduced, the database
schema must be altered. These schema changes can be time-consuming, error-prone,
and may require downtime, making the system less flexible for rapid expansion.

Additionally, storing customer reviews is difficult in a relational model.
Reviews naturally fit a nested structure with ratings, comments, and timestamps.
In RDBMS, this requires multiple related tables and joins, which complicates
queries and impacts performance.

## Section B: Advantages of MongoDB (NoSQL Benefits)

MongoDB addresses the limitations of relational databases by using a flexible
document-based schema. Each product can be stored as a JSON-like document with
only the attributes relevant to that product. For example, a laptop document
can include RAM and processor fields, while a shoe document can include size
and color, without affecting other product records. This eliminates the need
for frequent schema changes.

MongoDB also supports embedded documents, which allows related data to be
stored together. Customer reviews can be embedded directly within a product
document, including rating, comment, and timestamp. This reduces the need for
joins and makes data retrieval faster and simpler.

In terms of scalability, MongoDB supports horizontal scaling through sharding.
Data can be distributed across multiple servers, allowing the system to handle
large volumes of data and high traffic efficiently. This makes MongoDB suitable
for expanding product catalogs and growing user bases.

## Section C: Use-case Comparison (Trade-offs)

One disadvantage of using MongoDB instead of MySQL is weaker enforcement of
data consistency. Relational databases enforce strict schemas, constraints,
and relationships using primary and foreign keys. MongoDB relies more on
application-level validation, which can increase the risk of inconsistent or
duplicate data if not carefully managed.

Another drawback is the lack of support for complex relational queries.
MySQL is well-suited for scenarios requiring joins across multiple tables and
strong transactional guarantees. In MongoDB, handling complex relationships
often requires data duplication or multiple queries, which can complicate
application logic. Therefore, MongoDB may not be ideal for transaction-heavy
systems requiring strong consistency.

