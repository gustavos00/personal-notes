# Docker

## Important

**Host** - It is a computer, whether it's your home computer or a machine on AWS.  
**Kernel** - Creates a bridge between hardware and software (manages CPU, RAM, ...).  
**Binaries** - TBD
**Docker Tag** - It means the version of the image.

## Glossary

**pg** - Nickname for PostgreSQL.
**Keys** - Common attributes between tables.

---

## What is PostgreSQL?

PostgreSQL is a open-source relationnal database management system.
It supports the SQL standard and offers a wide range and advanced features like:
 - Suppost ACID transactions
 - Triggers
 - Views
 - Stored procedures.  
...

> What is a relational database?  

A relational database is a type of database management system that stores the data into tables with columns and rows.
Each table represents a specific entity or concept. The tables are related to each other through keys. 
Some examples of keys is the **primary key** and the **foreign key**.

> What is ACID transation?
ACID is a acronym that stands for **Atomicity**, **Consistency**, **Isolation**, and **Durability**.
 - **Atomicity** - Handles te transaction as a single, indivisible unit of work. If any part of the transaction fails, all the changes my that transaction are rolled back.
 - **Consistency** - Ensures that the transaction bring the database from one valid statoe to other valid state. A transaction should not violate any integrity contraints or leave the database in a inconsistent state.
 - **Isolation** - It make sure that current transactions will not interfere with each others. 
 - **Durability** - It guarantees that once a transaction is committed and changes are written to the database, they will persist even if the system fail or restart.

---
