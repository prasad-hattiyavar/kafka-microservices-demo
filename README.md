# kafka-microservices-demo
Event-driven microservices demo using Spring Boot and Apache Kafka (Order, Stock, Email services).

# Kafka Microservices Demo

A simple microservices architecture using **Spring Boot** and **Apache Kafka** to demonstrate event-driven communication between services.

## 📌 Architecture

- **Base-Domains**  
  Shared module containing DTOs (`Order`, `OrderEvent`) used across services.

- **Order-Service**  
  Exposes REST API `/api/v1/orders` to place orders. Publishes `OrderEvent` to Kafka.

- **Stock-Service**  
  Consumes `OrderEvent` from Kafka and simulates inventory updates.

- **Email-Service**  
  Consumes `OrderEvent` from Kafka and simulates sending customer notifications.

### Flow
1. Client places an order via REST API.  
2. Order-Service publishes `OrderEvent` → Kafka topic `order_topics`.  
3. Stock-Service consumes event → updates stock.  
4. Email-Service consumes event → sends email notification.  

---

## 📌 Tech Stack

- **Spring Boot** (Web, Kafka, JSON)  
- **Apache Kafka** (event broker)  
- **Lombok** (boilerplate reduction)  
- **Maven** (multi-module build)

---

## 📌 Setup Instructions

### 1. Start Kafka
```bash
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
