# firstjobapp

A simple Job Application REST API built with Spring Boot. It exposes CRUD endpoints for managing job postings, backed by an in-memory store.

## Tech Stack

- Java 21
- Spring Boot 3.5.13 (`spring-boot-starter-web`)
- Maven

## Project Structure

```
src/main/java/com/bhuvanesh/firstjobapp
├── FirstjobappApplication.java     # Spring Boot entry point
└── job
    ├── Job.java                    # Job model
    ├── JobController.java          # REST endpoints under /jobs
    ├── JobService.java             # Service interface
    └── impl
        └── JobServiceImpl.java     # In-memory implementation
```

## Getting Started

### Prerequisites

- JDK 21+
- Maven (or use the included Maven wrapper)

### Run the application

Using the Maven wrapper:

```bash
./mvnw spring-boot:run
```

On Windows:

```bash
mvnw.cmd spring-boot:run
```

The app starts on `http://localhost:8080`.

### Build

```bash
./mvnw clean package
```

The runnable jar is produced at `target/firstjobapp-0.0.1-SNAPSHOT.jar`.

### Run tests

```bash
./mvnw test
```

## API Endpoints

Base URL: `http://localhost:8080`

| Method | Endpoint      | Description              | Request Body |
|--------|---------------|--------------------------|--------------|
| GET    | `/jobs`       | Get all jobs             | —            |
| GET    | `/jobs/{id}`  | Get a job by ID          | —            |
| POST   | `/jobs`       | Create a new job         | `Job` JSON   |
| PUT    | `/jobs/{id}`  | Update an existing job   | `Job` JSON   |
| DELETE | `/jobs/{id}`  | Delete a job by ID       | —            |

### Job payload

```json
{
  "title": "Software Engineer",
  "description": "Build and maintain backend services",
  "minSalary": "60000",
  "maxSalary": "90000",
  "location": "Remote"
}
```

### Example requests

Create a job:

```bash
curl -X POST http://localhost:8080/jobs \
  -H "Content-Type: application/json" \
  -d '{"title":"Software Engineer","description":"Backend dev","minSalary":"60000","maxSalary":"90000","location":"Remote"}'
```

List all jobs:

```bash
curl http://localhost:8080/jobs
```

Get a job by ID:

```bash
curl http://localhost:8080/jobs/1
```

Update a job:

```bash
curl -X PUT http://localhost:8080/jobs/1 \
  -H "Content-Type: application/json" \
  -d '{"title":"Senior Software Engineer","description":"Lead backend dev","minSalary":"90000","maxSalary":"120000","location":"Remote"}'
```

Delete a job:

```bash
curl -X DELETE http://localhost:8080/jobs/1
```

## Notes

- Data is stored in memory and will be lost when the application restarts.
