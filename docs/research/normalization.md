# Database Normalization Documentation

## 1. Introduction

Database normalization is the process of organizing data into related tables to reduce unnecessary duplication and improve data consistency.

This project uses the RwandAir Flight Departure Dataset, which contains 500 simulated sample records and 9 fields.

The normalization process follows these stages:

- Unnormalized Form (UNF)
- First Normal Form (1NF)
- Second Normal Form (2NF)
- Third Normal Form (3NF)

The purpose is to organize flight information into related relational tables.

## 2. Unnormalized Form (UNF)

The original dataset stores all flight information together in one wide table.

It contains the following fields:

- FLIGHT_DATE
- FLIGHT
- ORIGIN
- DESTINATION
- AIRLINE
- SCHEDULED
- ACTUAL_DEPARTURE
- FLIGHT_STATUS
- DELAYED_MINUTES

### Sample records from the original dataset

| Date | Flight | Destination | Scheduled | Actual Departure | Status | Delay |
|---|---|---|---|---|---|---:|
| 2026-11-12 | WB822 | Brussels BRU | 8:30 PM | 8:40 PM | Landed | 10 |
| 2026-11-13 | WB360 | Dar-es-Salaam DAR | 12:50 AM | 4:14 AM | Delayed | 204 |
| 2026-11-14 | WB982 | Dubai DXB | 3:25 PM | 3:25 PM | Landed | 0 |
| 2026-11-15 | WB841 | Zanzibar ZNZ | 7:45 AM | 7:45 AM | En-Route | 0 |
| 2026-11-16 | WB438 | Zanzibar ZNZ | 9:35 PM | 11:01 PM | Delayed | 86 |

All five records have Kigali International Airport (KGL) as their origin and RwandAir as their airline.

The original dataset is already arranged in rows and columns. It does not contain nested lists or repeating groups within individual records.

## 3. First Normal Form (1NF)

First Normal Form requires each column to contain a single value and each record to represent one individual flight departure.

In this project:

- Each row represents one flight departure record.
- Each column contains an individual value.
- There are no repeating groups within a record.
- The flight departure records can be uniquely identified.

The five sample records shown in the UNF section satisfy these conditions.

**Dependency removed:** No repeating group was identified in the original flat dataset, so no structural split was required at this stage.

## 4. Second Normal Form (2NF)

Second Normal Form requires a table to be in 1NF and every non-key attribute to depend on the whole primary key.

The flight information is organized into separate entities:

### FLIGHT

Stores flight number, origin, destination and airline information.

| Flight ID | Flight Number | Origin | Destination |
|---:|---|---|---|
| 1 | WB822 | Kigali International Airport (KGL) | Brussels BRU |
| 2 | WB360 | Kigali International Airport (KGL) | Dar-es-Salaam DAR |
| 3 | WB982 | Kigali International Airport (KGL) | Dubai DXB |
| 4 | WB841 | Kigali International Airport (KGL) | Zanzibar ZNZ |
| 5 | WB438 | Kigali International Airport (KGL) | Zanzibar ZNZ |

### FLIGHT_SCHEDULE

Stores flight schedule information.

| Schedule ID | Flight ID | Flight Date | Scheduled Departure |
|---:|---:|---|---|
| 1 | 1 | 2026-11-12 | 8:30 PM |
| 2 | 2 | 2026-11-13 | 12:50 AM |
| 3 | 3 | 2026-11-14 | 3:25 PM |
| 4 | 4 | 2026-11-15 | 7:45 AM |
| 5 | 5 | 2026-11-16 | 9:35 PM |

### FLIGHT_PERFORMANCE

Stores actual departure time, flight status and delay information.

| Performance ID | Schedule ID | Actual Departure | Status | Delay Minutes |
|---:|---:|---|---|---:|
| 1 | 1 | 8:40 PM | Landed | 10 |
| 2 | 2 | 4:14 AM | Delayed | 204 |
| 3 | 3 | 3:25 PM | Landed | 0 |
| 4 | 4 | 7:45 AM | En-Route | 0 |
| 5 | 5 | 11:01 PM | Delayed | 86 |

The IDs in these sample tables illustrate the proposed relationships; the actual database uses generated identifiers.

**Dependency removed:** Flight details are separated from schedule and performance details so that information about a flight does not need to be repeated in every schedule and performance record.

## 5. Third Normal Form (3NF)

Third Normal Form requires a table to be in 2NF and non-key attributes not to depend on other non-key attributes.

The logical design separates the information into five related tables:

### 1. AIRLINE

Stores airline information.

| Airline ID | Airline Name |
|---:|---|
| 1 | RwandAir |

### 2. AIRPORT

Stores airport information, including airport names and codes.

| Airport ID | Airport Name | Airport Code |
|---:|---|---|
| 1 | Kigali International Airport | KGL |
| 2 | Brussels Airport | BRU |
| 3 | Dar-es-Salaam Airport | DAR |
| 4 | Dubai International Airport | DXB |
| 5 | Zanzibar Airport | ZNZ |

### 3. FLIGHT

Stores flight numbers and references to the airline and origin and destination airports.

### 4. FLIGHT_SCHEDULE

Stores flight dates and scheduled departure times.

### 5. FLIGHT_PERFORMANCE

Stores actual departure times, flight statuses and delay minutes.

**Dependency removed:** Airline details and airport details are separated into their own tables instead of being repeatedly stored with flight information. This removes transitive dependencies and reduces unnecessary duplication.

## 6. Logical Relationships

The proposed logical design contains five related tables:

- AIRLINE to FLIGHT: One airline can operate many flights.
- AIRPORT to FLIGHT: An airport can be the origin or destination of many flights.
- FLIGHT to FLIGHT_SCHEDULE: One flight can have many schedules.
- FLIGHT_SCHEDULE to FLIGHT_PERFORMANCE: Each schedule can have its performance record.

Primary keys identify records, while foreign keys connect related tables.

## 7. Field Mapping

| Original Field | Target Table | Target Column |
|---|---|---|
| FLIGHT_DATE | FLIGHT_SCHEDULE | FLIGHT_DATE |
| FLIGHT | FLIGHT | FLIGHT_NUMBER |
| ORIGIN | AIRPORT / FLIGHT | ORIGIN AIRPORT reference |
| DESTINATION | AIRPORT / FLIGHT | DESTINATION AIRPORT reference |
| AIRLINE | AIRLINE | AIRLINE_NAME |
| SCHEDULED | FLIGHT_SCHEDULE | SCHEDULED_DEPARTURE_TIME |
| ACTUAL_DEPARTURE | FLIGHT_PERFORMANCE | ACTUAL_DEPARTURE_TIME |
| FLIGHT_STATUS | FLIGHT_PERFORMANCE | FLIGHT_STATUS |
| DELAYED_MINUTES | FLIGHT_PERFORMANCE | DELAY_MINUTES |

### Required data type conversions

- FLIGHT_DATE: Text or Excel date to DATE.
- SCHEDULED: Time text to TIMESTAMP.
- ACTUAL_DEPARTURE: Time text to TIMESTAMP.
- DELAYED_MINUTES: Text or numeric value to NUMBER.

## 8. Benefits of Normalization

Normalization provides the following benefits:

- Reduces unnecessary duplication.
- Improves data consistency.
- Makes database maintenance easier.
- Helps prevent insertion, update and deletion anomalies.
- Maintains relationships between database tables.

## 9. Conclusion

The normalization process organizes the original flight dataset from a single wide table into a structured relational design.

The proposed logical design contains five related tables: AIRLINE, AIRPORT, FLIGHT, FLIGHT_SCHEDULE and FLIGHT_PERFORMANCE.

This design provides a foundation for managing airline schedules, monitoring flight performance and analysing delays using Oracle Database and PL/SQL.

**Implementation note:** The current Oracle database implementation contains FLIGHT, FLIGHT_SCHEDULE and FLIGHT_PERFORMANCE. AIRLINE and AIRPORT are additional tables in the proposed logical design and still need to be implemented if the five-table design is adopted.
