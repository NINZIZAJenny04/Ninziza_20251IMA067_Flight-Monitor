# Database Normalization Documentation

## 1. Introduction

Database normalization is the process of organizing data into separate tables to reduce unnecessary duplication and improve data consistency.

In this project, normalization was applied to organize airline flight information into three related tables.

## 2. First Normal Form (1NF)

First Normal Form requires each table column to contain a single value and each record to be uniquely identifiable.

In this project:
- Each table has a primary key.
- Each column stores individual values.
- There are no repeating groups of data.

Therefore, the tables satisfy the basic requirements of 1NF.

## 3. Second Normal Form (2NF)

Second Normal Form requires a table to be in 1NF and every non-key attribute to depend on the whole primary key.

In this project:
- Flight details are stored in the FLIGHT table.
- Flight schedule details are stored in the FLIGHT_SCHEDULE table.
- Flight performance details are stored in the FLIGHT_PERFORMANCE table.

Each table uses a single-column primary key, and its non-key attributes depend on that key.

## 4. Third Normal Form (3NF)

Third Normal Form requires a table to be in 2NF and non-key attributes not to depend on other non-key attributes.

In this project:
- Flight information is kept separately from schedule information.
- Schedule information is kept separately from performance information.
- Relationships are established using foreign keys.

This organization helps reduce unnecessary data duplication and update problems.

## 5. Database Tables

The project contains three main tables:

| Table | Purpose |
|---|---|
| FLIGHT | Stores flight numbers, origin, and destination |
| FLIGHT_SCHEDULE | Stores flight dates and scheduled departure times |
| FLIGHT_PERFORMANCE | Stores actual departure times, flight statuses, and delay minutes |

## 6. Relationships Between Tables

The tables are connected using primary keys and foreign keys:

- FLIGHT.FLIGHT_ID is referenced by FLIGHT_SCHEDULE.FLIGHT_ID.
- FLIGHT_SCHEDULE.SCHEDULE_ID is referenced by FLIGHT_PERFORMANCE.SCHEDULE_ID.

These relationships help maintain referential integrity and ensure that schedules and performance records are linked to existing records.

## 7. Benefits of Normalization

Normalization provides the following benefits:
- Reduces unnecessary duplication of information.
- Improves data consistency.
- Makes database maintenance easier.
- Helps prevent insertion, update, and deletion anomalies.
- Maintains relationships between database tables.

## 8. Conclusion

Normalization helped organize the Airline Flight Schedule and Delay Monitoring System into three related tables. This structure makes the database easier to manage, maintain, and use for flight schedule and delay analysis.
