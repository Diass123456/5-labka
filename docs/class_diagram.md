# «Фитнес клубты басқару ақпараттық жүйесі» - Class Diagram

```mermaid
classDiagram
    class Client {
        +int clientId
        +String name
        +String phone
        +String email
        +String password
        +register()
        +login()
        +viewSubscription()
        +bookTraining()
    }

    class Trainer {
        +int trainerId
        +String name
        +String specialization
        +String phone
        +login()
        +createTrainingPlan()
        +viewClients()
    }

    class Admin {
        +int adminId
        +String name
        +String login
        +String password
        +manageClients()
        +manageTrainers()
        +manageSubscriptions()
        +manageSchedule()
    }

    class Subscription {
        +int subscriptionId
        +String type
        +double price
        +Date startDate
        +Date endDate
        +String status
        +activate()
        +deactivate()
        +checkStatus()
    }

    class Training {
        +int trainingId
        +Date date
        +Time time
        +String type
        +int capacity
        +createTraining()
        +updateTraining()
        +cancelTraining()
    }

    class Payment {
        +int paymentId
        +double amount
        +Date date
        +String status
        +String paymentMethod
        +processPayment()
        +checkPaymentStatus()
    }

    Client "1" --> "0..*" Subscription : алады
    Client "1" --> "0..*" Payment : төлейді
    Subscription "1" --> "0..*" Payment : өңделеді
    Trainer "1" --> "0..*" Training : өткізеді
    Client "1" --> "0..*" Training : жазылады
    Admin ..> Client : басқарады
    Admin ..> Trainer : басқарады
    Admin ..> Subscription : басқарады
    Admin ..> Training : басқарады