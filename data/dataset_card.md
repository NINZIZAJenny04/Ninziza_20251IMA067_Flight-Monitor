# Dataset Card

## 1. Dataset Information

- **Dataset name:** RwandAir Flight Departure Dataset 2026
- **File name:** RwandAir_Flight_Departure_Dataset_2026.xlsx
- **Format:** Excel (.xlsx)
- **Number of records:** 500
- **Number of columns:** 9
- **Date range covered:** 12 November 2026 – 19 November 2026
- **Dataset type:** Simulated sample data for academic purposes.

## 2. Source and Licence

- **Source:** Simulated dataset prepared for the Airline Flight Schedule and Delay Monitoring System project.
- **Source link:** Not applicable; this is not an externally downloaded dataset.
- **Licence:** Created for educational and academic project use.

## 3. What One Record Represents

One record represents a flight departure entry containing information about the flight number, departure date, origin, destination, airline, scheduled departure time, actual departure time, flight status and delay duration.

## 4. Dataset Fields

The dataset contains the following nine fields:

1. FLIGHT_DATE
2. FLIGHT
3. ORIGIN
4. DESTINATION
5. AIRLINE
6. SCHEDULED
7. ACTUAL_DEPARTURE
8. FLIGHT_STATUS
9. DELAYED_MINUTES

## 5. Data Quality Summary

- Total records: 500
- Unique flight numbers: 394
- Unique routes: 24
- Duplicate combinations of flight date, flight number and scheduled time: 0

### Flight Status Distribution

| Flight Status | Records |
|---|---:|
| En-Route | 182 |
| Delayed | 132 |
| Landed | 179 |
| Scheduled | 7 |
| **Total** | **500** |

The dataset was checked for duplicate flight records and examined for flight status and delay information.

## 6. Date Collected

The dataset covers the period from 12 November 2026 to 19 November 2026. The exact date the file was prepared or obtained is not recorded.

## 7. Purpose of the Dataset

The dataset is used to design and develop a relational database system for managing flight schedules, monitoring flight delays and analysing flight performance using Oracle Database and PL/SQL.
