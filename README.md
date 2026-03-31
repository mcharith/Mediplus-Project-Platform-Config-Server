# Config-Server

---

A centralized external configuration server for the **Mediplus microservices ecosystem**.  
It serves configuration properties to all registered services from a single source, enabling environment-specific settings without requiring redeployment.

---

## 👤 Student Information

- **Student Name:** Charith Mihiranga Siriwardana
- **Student Number:** 2301691075
- **Slack:** https://ijse-eca-hdse-69-70.slack.com/team/U0AHD5TQ4H5
- **GCP Project ID:** its-2130-eca-gdse-491417

---

## 📖 About

The Config-Server is a core component of the microservice architecture, responsible for managing and distributing configuration across all services.  
Instead of hardcoding configurations within each service, this server provides a centralized approach, improving consistency, maintainability, and scalability.

It uses **Spring Cloud Config Server** with a native filesystem backend to load configuration files and deliver them dynamically to client services during startup.  
This ensures that all services remain synchronized and can easily adapt to different environments (development, staging, production) without rebuilding or redeploying the application.

---

## 🛠️ Tech Stack

| Technology                   | Details                          |
|-----------------------------|----------------------------------|
| Java                        | 25                               |
| Spring Boot                 | 4.0.3                            |
| Spring Cloud                | 2025.1.0                         |
| Spring Cloud Config Server  | Native filesystem backend        |
| Spring Boot Actuator        | Health & management endpoints    |

---

## ⚙️ Service Details

| Property    | Value         |
|-------------|---------------|
| Port        | 9100          |
| Artifact ID | Config-Server |
| Group ID    | lk.ijse.eca   |

---

## ⚡ How It Works

The Config-Server uses a **native filesystem backend**, loading configuration files from the application’s classpath.

- Each microservice fetches its configuration during startup
- Configurations are organized by service name
- Shared configurations can be reused across multiple services
- Changes can be applied centrally without modifying individual services

---

## 📁 Configuration Layout

```bash
src/main/resources/configurations/
├── application.yaml
│   # Shared configuration (Eureka URL, logging, common settings)
├── platform/
│   ├── api-gateway.yaml
│   │   # API Gateway routes and CORS configuration
│   └── service-registry.yaml
│       # Eureka Server configuration
└── services/
    ├── patient-service.yaml
    │   # PostgreSQL configuration
    ├── doctor-service.yaml
    │   # MongoDB configuration
    └── appointment-service.yaml
        # MySQL configuration
```

---

## 🚀 Getting Started

### ⚠️ Important

Config-Server **must be started first** before any other service, as all microservices fetch their configuration from this server during startup.

---

### ▶️ Run the Service

```bash
./mvnw spring-boot:run
```

---

### 🌐 Access the Server

```
http://localhost:9100
```

---

### 🔍 Verify Configuration

You can verify that configurations are being served correctly using:

```
http://localhost:9100/{service-name}/default
```

👉 Example:

```
http://localhost:9100/patient-service/default
```
