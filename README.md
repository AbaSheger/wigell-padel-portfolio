# Wigell Padel Booking System

A microservices-based padel court booking system built with Spring Boot, Eureka for service discovery, and an API Gateway for routing.

## Architecture

```mermaid
graph TD
    Client[Client] --> Gateway[API Gateway]
    Gateway --> Eureka[Eureka Server]
    Gateway --> WigellPadel[Wigell Padel Service]
    WigellPadel --> Eureka
    
    subgraph "Wigell Padel Service"
        WigellPadel --> Controllers[Controllers]
        Controllers --> Services[Services]
        Services --> Repositories[Repositories]
        Repositories --> Database[(MySQL Database)]
    end
    
    subgraph "Service Components"
        Services --> FieldService[FieldService]
        Services --> BookingService[BookingService]
    end
    
    subgraph "Entity Model"
        Repositories --> FieldEntity[Field]
        Repositories --> BookingEntity[Booking]
    end
    
    classDef service fill:#f9f,stroke:#333,stroke-width:2px;
    classDef database fill:#bdf,stroke:#333,stroke-width:2px;
    class WigellPadel,Gateway,Eureka service;
    class Database database;