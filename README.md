# Microservices Product Sales

![Java 17](https://img.shields.io/badge/Java-17-blue.svg)
![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-brightgreen)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

A modular microservices-based system for managing products and sales, built using **Spring Boot 3**, **Java 17**, and following **Clean Architecture** principles. Services communicate via **OpenFeign** to ensure loose coupling and scalability.

---

## 📌 Overview

This project includes two independent microservices:

- `products`: Manages product data and inventory.
- `sales`: Handles sales operations and updates product stock.

Each service is self-contained, maintainable, and independently deployable, designed to fit into a scalable distributed system.

---

## 📦 Microservices

### 💾 `products` (Product Service)

Responsible for managing product information and stock.

**Core features:**

- Create new products  
- Update or delete existing products  
- Manage product stock levels  

### 💸 `sales` (Sales Service)

Responsible for managing and recording sales.

**Core features:**

- Register sales transactions  
- Automatically decrease stock via the `products` service  
- Maintain a detailed sales history  

---

## 🧱 Project Structure

<details>
<summary>Click to expand</summary>

```text
microservices-product-sales/
├── products/
│   └── src/main/java/com/pragma/
│       ├── domain/             # Core domain models
│       ├── application/        # Use cases and service interfaces
│       ├── infrastructure/
│       │   ├── input/          # REST controllers (input adapters)
│       │   ├── output/         # Feign clients, external adapters
│       │   └── persistence/    # Database access
│       └── ProductsApplication.java
├── sales/
│   └── src/main/java/com/pragma/
│       ├── domain/
│       ├── application/
│       ├── infrastructure/
│       └── SalesApplication.java
````

</details>

This structure follows **Clean Architecture**:
**Domain → Application → Infrastructure**

---

## 🚀 Getting Started

### Prerequisites

* Java 17
* Maven 3.x
* Docker (optional for database/service discovery)
* Postman or curl for API testing

### Running the services

```bash
# Start the products service
cd products
./mvnw spring-boot:run
```

```bash
# Start the sales service
cd sales
./mvnw spring-boot:run
```

> ⚠️ Ensure both services are running. Configure OpenFeign endpoints appropriately if you're not using a discovery server like Eureka.

---

## 🧪 Testing

Each service includes unit and integration tests:

```bash
./mvnw test
```

## 📶 Inter-Service Communication

This project uses **Spring Cloud OpenFeign** to enable declarative REST communication between microservices.

* `sales` calls the `products` microservice to update stock after a successful transaction.

---

## 🔧 Tech Stack

* Java 17
* Spring Boot 3.x
* Spring Data JPA
* Spring Web / REST
* Spring Cloud OpenFeign
* Maven

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 🔗 Related Resources

* [Spring Boot Documentation](https://docs.spring.io/spring-boot/)
* [OpenFeign Docs](https://spring.io/projects/spring-cloud-openfeign)
* [Clean Architecture by Uncle Bob](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)

---
