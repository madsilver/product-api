# Next Steps

The project can now evolve to cover more advanced Spring Boot topics.

## API

* Find product by ID
* Update product
* Delete product

## DTOs

Replace entities in the API with:

* ProductRequest
* ProductResponse

Learn:

* Records
* Mapping
* API contracts

---

## Validation

Add Bean Validation.

Topics:

* `@Valid`
* `@NotBlank`
* `@Positive`
* `@Size`

---

## Exception Handling

Implement:

```
@ControllerAdvice
```

Topics:

* Global exception handling
* Custom exceptions
* Consistent error responses

---

## Persistence

Learn custom repository methods.

Examples:

```
findByName()

findByPriceGreaterThan()

findByNameContainingIgnoreCase()
```

Understand how Spring generates SQL from method names.

---

## Transactions

Learn:

```
@Transactional
```

Topics:

* Transaction boundaries
* Rollback
* ACID

---

## Testing

Implement:

* Unit tests
* Repository tests
* Controller tests
* Integration tests using Testcontainers

---

## API Documentation

Generate OpenAPI documentation using Springdoc.

Provide:

* Swagger UI
* OpenAPI specification

---

## Production Readiness

Topics to explore:

* Actuator
* Health checks
* Metrics
* Prometheus
* Structured logging
* Docker
* Docker Compose
* Profiles
* External configuration
* Flyway database migrations
* Kubernetes deployment

---

# Learning Outcomes

By completing this project, you will have practiced:

* Spring Boot fundamentals
* Dependency Injection
* Bean lifecycle
* Spring MVC
* REST API development
* Spring Data JPA
* Hibernate ORM
* PostgreSQL integration
* Docker
* Spring Profiles
* Configuration management
* Structured logging
* Layered architecture
* Separation of concerns
* IntelliJ HTTP Client
* Basic production-ready application structure
