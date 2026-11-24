# Data Dictionary

## 1. Introduction

This data dictionary describes the five main entities in the Airline Flight Schedule and Delay Monitoring System. It explains the purpose of each column, its primary or foreign key role, and whether the information is required or unique.

The logical design is based on the RwandAir flight departure sample dataset.

## 2. AIRLINE Table

Stores information about airlines.

| Column | Meaning | Key | Required | Unique |
|---|---|---|---|---|
| AIRLINE_ID | Identifies each airline | PK | Yes | Yes |
| AIRLINE_NAME | Name of the airline | — | Yes | Yes |

## 3. AIRPORT Table

Stores information about airports.

| Column | Meaning | Key | Required | Unique |
|---|---|---|---|---|
| AIRPORT_ID | Identifies each airport | PK | Yes | Yes |
| AIRPORT_NAME | Full name of the airport | — | Yes | No |
| AIRPORT_CODE | Three-letter airport code | — | Yes | Yes |

## 4. FLIGHT Table

Stores information about each flight.

| Column | Meaning | Key | Required | Unique |
|---|---|---|---|---|
| FLIGHT_ID | Identifies each flight | PK | Yes | Yes |
| FLIGHT_NUMBER | Airline flight number | — | Yes | Yes |
| AIRLINE_ID | Identifies the airline operating the flight | FK | Yes | No |
| ORIGIN_AIRPORT_ID | Identifies the departure airport | FK | Yes | No |
| DESTINATION_AIRPORT_ID | Identifies the arrival airport | FK | Yes | No |

## 5. FLIGHT_SCHEDULE Table

Stores scheduled departure information.

| Column | Meaning | Key | Required | Unique |
|---|---|---|---|---|
| SCHEDULE_ID | Identifies each flight schedule | PK | Yes | Yes
