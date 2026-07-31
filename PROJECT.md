# Spring Boot Product API – Development Guide

This document summarizes the development of the **Product API** project, explaining not only *what* was implemented, 
but also *why* each step was taken.

---

# 1. Verify the Development Environment

Before creating the project, verify that Java 21 is installed.

```bash
java -version
```

---

# 2. Generate the Project

Generate a new project using **Spring Initializr**.

Configuration:

* Project: Maven
* Language: Java
* Spring Boot: 4.1
* Group: `com.example`
* Artifact: `product-api`
* Packaging: Jar
* Java: 21

Dependencies:

* Spring Web
* Spring Data JPA
* PostgreSQL Driver
* Validation

The generated project already includes Maven configuration and a runnable Spring Boot application.

---

# 3. Configure PostgreSQL

Create a `docker-compose.yaml` file.

```yaml
services:
  postgres:
    image: postgres:17
    environment:
      POSTGRES_DB: productdb
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: postgres
    ports:
      - "5432:5432"
```

Start the database.

```bash
docker compose up -d
```

---

# 4. Configure Spring Boot

Organize the configuration by environment.

```
application.yaml        // Shared configuration
application-dev.yaml    // Development-specific configuration
application-prod.yaml   // Production configuration
```
---

# 5. Understand Spring Boot Startup

Run the application. Important things to verify:

* PostgreSQL connection
* Hibernate initialization
* Repository scanning
* Embedded Tomcat startup

Example:

```
Found 1 JPA repository interface.
```

Understanding startup logs is an important debugging skill.

---

# 6. Create the Entity

```
Product
```

Responsibilities:

* Represent a database table.
* Map object fields to columns.

Concepts learned:

* `@Entity`
* `@Id`
* `@GeneratedValue`
* Constructor required by JPA
* Why entities should be mutable
* Why entities are usually classes instead of records
* Why `equals()` and `hashCode()` should be used carefully on JPA entities

---

# 7. Create the Repository

```
ProductRepository
```

```java
public interface ProductRepository
        extends JpaRepository<Product, Long> {
}
```

Concepts learned:

* Spring Data JPA
* Repository pattern
* Dynamic proxy generation
* Automatic implementation creation
* CRUD methods inherited from `JpaRepository`

Examples:

* save()
* findAll()
* findById()
* deleteById()

---

# 8. Create the Service Layer

```
ProductService
```

Responsibilities:

* Business rules.
* Coordinate persistence.
* Keep controllers thin.

Concepts learned:

* `@Service`
* Dependency Injection
* Constructor Injection
* Bean lifecycle
* Separation of concerns

---

# 9. Create the REST Controller

```
ProductController
```

Endpoints:

```
POST /products
GET  /products
```

Concepts learned:

* `@RestController`
* `@RequestMapping`
* `@PostMapping`
* `@GetMapping`
* `@RequestBody`

---

# 10. Test the API

Create:

```
requests.http
```

Use the IntelliJ IDEA HTTP Client to test the API.

Advantages:

* Version controlled
* Easy to maintain
* No external tools required
* Great for small projects

---

# 11. Configure Logging

Development:

* Human-readable logs.

Production:

```yaml
logging:
  structured:
    format:
      console: ecs
```

Concepts learned:

* Structured logging
* ECS format
* ELK compatibility
* Environment-specific logging

---

# 12. Hibernate Concepts

Topics studied:

* What is a Dialect?
* Automatic dialect detection
* Why explicitly configuring the dialect can improve startup diagnostics
* Database metadata
* DDL generation

---

# 13. Spring Data JPA Concepts

Topics studied:

* Why no repository implementation is required
* Dynamic proxy generation
* Reflection
* Runtime implementation creation
* Repository registration
