
```mermaid
erDiagram
    clients {
        int client_id PK
        string name
        string phone
        string email
        string password
    }

    trainers {
        int trainer_id PK
        string name
        string specialization
        string phone
    }

    subscriptions {
        int subscription_id PK
        int client_id FK
        string type
        decimal price
        date start_date
        date end_date
        string status
    }

    trainings {
        int training_id PK
        int trainer_id FK
        int client_id FK
        date date
        time time
        string type
        int capacity
    }

    payments {
        int payment_id PK
        int client_id FK
        int subscription_id FK
        decimal amount
        datetime date
        string status
        string payment_method
    }

    clients ||--o{ subscriptions : "алады"
    clients ||--o{ payments : "төлейді"
    subscriptions ||--o{ payments : "өңделеді"
    trainers ||--o{ trainings : "өткізеді"
    clients ||--o{ trainings : "жазылады"