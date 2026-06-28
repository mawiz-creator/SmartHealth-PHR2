# SmartHealth PHR System

Welcome to the official repository for **SmartHealth** — an AI-Powered Web-Based Personal Health Record System featuring predictive analytics, real-time notifications, and secure data handling.

## 📊 Database Schema (Entity-Relationship Diagram)

```mermaid
erDiagram
    USERS {
        uuid id PK
        text email UK
        text role
        timestamp created_at
    }

    PATIENT_PROFILES {
        uuid id PK
        uuid user_id FK
        text first_name
        text last_name
        date date_of_birth
        text gender
    }

    HEALTH_METRICS {
        uuid id PK
        uuid patient_id FK
        int blood_pressure_systolic
        int blood_pressure_diastolic
        int blood_sugar
        timestamp recorded_at
    }

    REMINDERS {
        uuid id PK
        uuid patient_id FK
        text title
        timestamp scheduled_time
        boolean is_sent
    }

    USERS ||--|| PATIENT_PROFILES : "has profile"
    PATIENT_PROFILES ||--o{ HEALTH_METRICS : "logs"
    PATIENT_PROFILES ||--o{ REMINDERS : "receives"
