# Ninziza_20251IMA067_Flight-Monitor

1. Student Information
- Full Name: Ninziza Jenny Deborah
- Student ID: 20251IMA067
- Course Code: INSY 8311
- Course Name: Database Development with PL/SQL
- Project Type: Individual Project
- Academic Year: 2026-2027

2. Project Description

Airline flight delays and schedule changes can cause inconvenience to passengers and difficulties in monitoring flight operations. This project aims to develop an Oracle database system to manage flight schedules, monitor delays, and record flight statuses using RwandAir as a case study.

3. Problem Statement

Airline operations involve managing many flights, routes, schedules, and departure times. Without an organized system, monitoring flight delays and maintaining accurate flight records can become difficult.

4. Project Objectives

The main objectives of this project are:

1. To manage airline and airport information.
2. To store and organize flight schedules.
3. To monitor delayed, cancelled, and on-time flights.
4. To record flight delay durations and reasons.
5. To generate reports about flight operations.
6. To develop PL/SQL programs that automate flight monitoring.
   
    5. Business Process

The business process involves four main actors:

1. Passenger
2. Airline Staff
3. Manager
4. Aviation System

The process begins when a passenger receives a flight delay notification. The passenger reviews the available options and submits a preferred choice. Airline staff verify the request and forward exceptional requests to the manager for approval or rejection. The Aviation System monitors flight status, records delays, processes passenger requests and updates flight records.

### Business Process Diagram

![Airline Flight Schedule and Delay Monitoring System BPMN Diagram](docs/business_process_diagram.png)

6. Data Source

The project will use publicly available flight information
from the following sources:

1. RwandAir Daily Flight Status:
   https://www.rwandair.com/rw-en/daily-flight-status

2. Airportia:
   https://www.airportia.com/airlines/rwandair/departures/

These sources provide flight numbers, routes, scheduled
times, actual times, and flight statuses.

The collected records will be used as sample data for
the RwandAir case study. They do not represent the
airline's complete internal operational database.

Additional supplementary airline performance data may
be obtained from the U.S. Bureau of Transportation
Statistics:
https://www.transtats.bts.gov/ONTIME/

The supplementary dataset will be used only if suitable
data and permitted educational use are confirmed.
7. Planned Innovation

Innovation: Automatic Flight Delay Alert and Monitoring Dashboard

Tool: Microsoft Power BI

The system will identify delayed, cancelled, and on-time flights, calculate delay durations, and display flight performance statistics through an interactive dashboard. Microsoft Power BI will be used to visualize flight information, monitor delays, and generate useful reports to support flight operations monitoring.

8. Planned Database Tables

The project will initially include the following tables:

1. AIRLINES – Stores airline information.
2. AIRPORTS – Stores airport names and locations.
3. ROUTES – Stores departure and destination information.
4. FLIGHTS – Stores flight schedules and statuses.
5. FLIGHT_DELAYS – Stores flight delay details and reasons.

9. Planned PL/SQL Features
   
The project will use the following Oracle PL/SQL features:

- Procedures – To manage flight information.
- Functions – To calculate flight delay durations.
- Cursors – To retrieve and display flight records.
- Packages – To organize related PL/SQL programs.
- Triggers – To automatically update flight statuses and record delays.
- Exception Handling – To handle database errors.

10. Expected Results
    
The expected result is a functional Oracle database system that organizes airline flight information, monitors flight delays, and generates useful flight reports. The system will also demonstrate how PL/SQL can automate important database operations.

11. Project References

- U.S. Bureau of Transportation Statistics: https://www.transtats.bts.gov/ONTIME/
- Oracle Database Documentation: https://docs.oracle.com/en/database/oracle/oracle-database/21/

Additional research references will be documented in "docs/research/research_log.md".
