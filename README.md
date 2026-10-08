# cadastro-usuario: user registration REST API

A small REST API for registering users, built to practise a layered Spring Boot architecture (controller, service, repository) with Spring Data JPA.

## Tech stack

- Java 25, Spring Boot 4
- Spring Web MVC, Spring Data JPA
- H2 in-memory database
- Lombok, Maven

## Endpoints

Base path: `/usuario`

| Method | Parameters | Description |
|---|---|---|
| POST | body: `{ "email", "nome", "telefone" }` | Create a user |
| GET | `?email=` | Find a user by e-mail |
| PUT | `?id=` and a body with the fields to change | Partial update by id |
| DELETE | `?email=` | Delete a user by e-mail |

## Running locally

```bash
./mvnw spring-boot:run
```

The API starts on `http://localhost:8081`. The H2 console is available at `/h2-console` (JDBC URL `jdbc:h2:mem:usuario`, user `sa`, empty password).

Example:

```bash
curl -X POST http://localhost:8081/usuario \
  -H "Content-Type: application/json" \
  -d '{"email":"ana@example.com","nome":"Ana","telefone":"51999990000"}'

curl "http://localhost:8081/usuario?email=ana@example.com"
```

## Project structure

```text
src/main/java/com/javaDeus/cadastro_usuario/
|-- controller/                  # REST endpoints
|-- business/                    # service layer
`-- infrastructure/
    |-- entitys/                 # JPA entity
    `-- repository/              # Spring Data repository
```
