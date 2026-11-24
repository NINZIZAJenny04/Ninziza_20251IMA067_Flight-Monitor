# Data Source Documentation

## 1. Introduction

This project uses a flight dataset to develop an Airline Flight Schedule and Delay Monitoring System based on the RwandAir case study.

The dataset contains 500 simulated flight records prepared for database development, testing, and analysis. These records are not verified actual RwandAir operational flight records.

## 2. Data Source

The dataset was prepared as sample data representing airline flight departures. It was stored in an Excel file named `RwandAir_Flight_Departure_Dataset_2026.xlsx` and converted into CSV format for importing into Oracle Database.

The CSV file used was `RwandAir_Flight_Departure_2026_Oracle.csv`.

## 3. Dataset Description

The dataset contains 500 records and nine columns:

| Column | Description |
|---|---|
| FLIGHT_DATE | Date of the flight |
| FLIGHT | Flight number |
| ORIGIN | Departure airport |
| DESTINATION | Arrival airport |
| AIRLINE | Airline name |
| SCHEDULED | Scheduled departure time |
| ACTUAL_DEPARTURE | Actual departure time |
| FLIGHT_STATUS | Current flight status |
| DELAYED_MINUTES | Flight delay duration in minutes |

## 4. Data Preparation

The dataset was prepared in Excel and converted into CSV format to make it suitable for Oracle Database import.

The data was then imported into the Oracle table named `RWA_FLIGHT_DATA`.

## 5. Data Loading into Oracle

The imported dataset was used to populate three main database tables:

- FLIGHT
- FLIGHT_SCHEDULE
- FLIGHT_PERFORMANCE

The database contains 394 unique flights, 500 flight schedules, and 500 flight performance records.

## 6. Purpose of the Dataset

The dataset supports the analysis of flight schedules, flight statuses, delayed flights, delay durations, and flight routes.

It helps demonstrate how a database system can organize and monitor airline flight information.
