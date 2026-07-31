# Product API

A simple REST API built with Spring Boot to demonstrate the development of a Java application following a layered architecture.

The project is intended as a learning exercise and showcases the main components of a typical Spring Boot application:

* Controller
* Service
* Repository
* Entity

Persistence is implemented using Spring Data JPA with PostgreSQL as the database.

## Technologies

* Java 21
* Spring Boot 4.1
* Spring Web
* Spring Data JPA
* PostgreSQL 17
* Maven
* Docker Compose

## Prerequisites

* Java 21
* Maven 3.9+
* Docker and Docker Compose

## Running the Application

Start the application:

```bash
mvn spring-boot:run
```

The application will be available at:

```text
http://localhost:8080
```

## API Endpoints

Example requests for all available endpoints can be found in the `requests.http` file located in the project root.

The file is compatible with the IntelliJ IDEA HTTP Client and can be used to execute requests directly from the IDE.


## Configuration

Application settings are organized using Spring Profiles.

Configuration files:

* `application.yaml` – shared configuration
* `application-dev.yaml` – development environment
* `application-prod.yaml` – production environment

The active profile can be selected using:

```bash
SPRING_PROFILES_ACTIVE=dev
```

or

```bash
./mvnw spring-boot:run -Dspring-boot.run.profiles=dev
```

## Database

The project uses PostgreSQL together with Hibernate.

During development, the database schema is updated automatically:

```yaml
spring:
  jpa:
    hibernate:
      ddl-auto: update
```

For production environments, it is recommended to use:

```yaml
spring:
  jpa:
    hibernate:
      ddl-auto: validate
```

along with a database migration tool such as **Flyway** or **Liquibase**.

## Roadmap

* Introduce DTOs (`ProductRequest` and `ProductResponse`)
* Add Bean Validation using `@Valid`
* Implement "Find by ID"
* Implement update and delete operations
* Add global exception handling with `@ControllerAdvice`
* Generate OpenAPI/Swagger documentation
* Add unit and integration tests
