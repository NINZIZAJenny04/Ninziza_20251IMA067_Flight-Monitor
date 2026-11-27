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

Thank you. I've checked your entire document against the Phase II requirements.

Good news: **most of the required sections are already there.** We don't need to start again. However, a few things need correction before we can consider it complete.

### **What needs correction**

1. **UNF:** The sample table is missing two original fields: `ORIGIN` and `AIRLINE`.
2. **1NF:** We should clarify how each original flight departure record is uniquely identified.
3. **2NF:** We need to explain the partial dependency more clearly.
4. **3NF:** We need to make the airport and airline relationships more precise.
5. **Field mapping:** Some target columns are not specified clearly enough.
6. **Data type conversions:** We need to explain how the time values are converted for Oracle.

Let's correct these one at a time.

### **Step 1: Correct the UNF sample table**

In your document, under **2. Unnormalized Form (UNF)**, replace the existing sample table with this one:

| Date       | Flight | Origin     | Destination       | Airline  | Scheduled | Actual Departure | Status   | Delay |
| ---------- | ------ | ---------- | ----------------- | -------- | --------- | ---------------- | -------- | ----- |
| 2026-11-12 | WB822  | Kigali KGL | Brussels BRU      | RwandAir | 8:30 PM   | 8:40 PM          | Landed   | 10    |
| 2026-11-13 | WB360  | Kigali KGL | Dar-es-Salaam DAR | RwandAir | 12:50 AM  | 4:14 AM          | Delayed  | 204   |
| 2026-11-14 | WB982  | Kigali KGL | Dubai DXB         | RwandAir | 3:25 PM   | 3:25 PM          | Landed   | 0     |
| 2026-11-15 | WB841  | Kigali KGL | Zanzibar ZNZ      | RwandAir | 7:45 AM   | 7:45 AM          | En-Route | 0     |
| 2026-11-16 | WB438  | Kigali KGL | Zanzibar ZNZ      | RwandAir | 9:35 PM   | 11:01 PM         | Delayed  | 86    |

This now shows all **9 original dataset fields**.

Make this replacement and tell me **Done**. Then we'll move to the next correction.

All five records have Kigali International Airport (KGL) as their origin and RwandAir as their airline.

The original dataset is already arranged in rows and columns. It does not contain nested lists or repeating groups within individual records.

## 3. First Normal Form (1NF)

Each flight departure record can be identified using the combination of FLIGHT_DATE, FLIGHT and SCHEDULED. This combination was checked for duplicate records in the dataset, and no duplicates were found.
## 4. Second Normal Form (2NF)


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

**Dependency removed:** In the original dataset, flight details such as ORIGIN, DESTINATION and AIRLINE depend on the FLIGHT number rather than the complete flight departure key. These details are separated into the FLIGHT table to remove partial dependency and reduce repetition.

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
