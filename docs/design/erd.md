# Entity Relationship Diagram (ERD)

## Airline Flight Schedule and Delay Monitoring System

The ERD shows five entities and their relationships.

```mermaid
erDiagram
    AIRLINE ||--o{ FLIGHT : operates
    AIRPORT ||--o{ FLIGHT : origin
    AIRPORT ||--o{ FLIGHT : destination
    FLIGHT ||--o{ FLIGHT_SCHEDULE : has
    FLIGHT_SCHEDULE ||--o| FLIGHT_PERFORMANCE : records

    AIRLINE {
        int AIRLINE_ID PK
        string AIRLINE_NAME
    }

    AIRPORT {
        int AIRPORT_ID PK
        string AIRPORT_NAME
        string AIRPORT_CODE
    }

    FLIGHT {
        int FLIGHT_ID PK
        string FLIGHT_NUMBER
        int AIRLINE_ID FK
        int ORIGIN_AIRPORT_ID FK
        int DESTINATION_AIRPORT_ID FK
    }

    FLIGHT_SCHEDULE {
        int SCHEDULE_ID PK
        int FLIGHT_ID FK
        date FLIGHT_DATE
        datetime SCHEDULED_DEPARTURE_TIME
    }

    FLIGHT_PERFORMANCE {
        int PERFORMANCE_ID PK
        int SCHEDULE_ID FK
        datetime ACTUAL_DEPARTURE_TIME
        string FLIGHT_STATUS
        int DELAY_MINUTES
    }
```

## Relationship Explanation

1. One airline can operate many flights.
2. One airport can be the origin of many flights.
3. One airport can be the destination of many flights.
4. One flight can have many schedules.
5. One schedule can have zero or one performance record.

**Note:** PK means Primary Key and FK means Foreign Key. The crow's-foot symbols show the relationships and cardinality between entities.
