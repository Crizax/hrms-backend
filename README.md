# HRMS (Human Resource Management System)


## English

### Project Description

HRMS (Human Resource Management System) is a Spring Boot REST API for managing job postings, employer registrations, candidate applications, and hiring workflows. It implements DTO, Request-Response Pattern, Validation, and Global Exception Handling.

### Features

- **City Management** — Add and list cities with unique name constraint
- **Job Position Management** — Add and list job positions
- **Employer Management** — Register and list employers
- **Candidate Management** — Register and list job seekers
- **Job Advertisement Management** — Add, list, and filter job advertisements
- **Job Application Management** — Candidates can apply for job advertisements
- **Global Exception Handling** — Consistent error responses via `@ControllerAdvice`
- **Field Validation** — Jakarta Validation annotations (`@NotBlank`, `@Size`, `@Email`, `@Future`)

### Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 17 |
| Framework | Spring Boot 3 |
| ORM | Spring Data JPA / Hibernate |
| Database | PostgreSQL |
| Testing | JUnit 5, MockMvc |
| Utilities | Lombok, Jackson, Jakarta Validation |

### Architecture

```
controller/     → REST API endpoints
service/        → Business logic
repository/     → Database access (Spring Data JPA)
entity/         → Database table mappings
dto/            → API response objects
request/        → Incoming request models
core/           → Shared result structures (Result, DataResult, SuccessResult, ErrorResult)
```

### API Endpoints

#### Cities
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/cities/add` | Add a new city |
| GET | `/api/cities/getAll` | List all cities |

#### Employers
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/employers/register` | Register a new employer |
| GET | `/api/employers/getAll` | List all employers |

#### Job Seekers
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/candidateController/register` | Register a new candidate |
| GET | `/api/candidateController/getAll` | List all candidates |

#### Job Advertisements
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/jobAdvertisements/add` | Add a new job advertisement |
| GET | `/api/jobAdvertisements/getAll` | List all job advertisements |

#### Job Applications
| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/jobApplications/apply` | Apply for a job advertisement |

### Sample Requests

**Register Employer**
```json
POST /api/employers/register
{
  "companyName": "Tech Solutions Ltd.",
  "companyWebPage": "https://techsolutions.com",
  "email": "contact@techsolutions.com",
  "phoneNumber": "+90-555-123-4567",
  "password": "password123",
  "confirmPassword": "password123"
}
```
**Candidate Registration:**
```json
{
    "name": "Aysu",
    "lastName": "Ay",
    "nationalId": "12345678901",
    "birthDate": 1995,
    "email": "aysu@example.com",
    "password": "password123",
    "confirmPassword": "password123"
}

**Add Job Advertisement**
```json
POST /api/jobAdvertisements/add
{
  "description": "We are looking for a Java Backend Developer with Spring Boot experience.",
  "openPositionCount": 2,
  "minSalary": 30000,
  "maxSalary": 50000,
  "applicationDeadline": "2025-12-31",
  "jobPositionId": 1,
  "cityId": 1,
  "employerId": 1
}
```

### Tests

27 unit and integration tests written with JUnit 5 and MockMvc.

| Test Class | Type | What it tests |
|---|---|---|
| `CityDaoTest` | Unit | Save, duplicate city name constraint |
| `CityControllerTest` | Integration | API responses, validation |
| `EmployerDaoTest` | Unit | Save, duplicate email constraint |
| `JobSeekerDaoTest` | Unit | Save, duplicate email and national ID |
| `JobPositionDaoTest` | Unit | Save and retrieve |
| `JobAdvertisementDaoTest` | Unit | Save with relations |
| `JobAdvertisementControllerTest` | Integration | Advertisement API responses |
| `JobApplicationDaoTest` | Unit | Application save and status |

```bash
mvn test
# Tests run: 27, Failures: 0, Errors: 0
```



API will be available at `http://localhost:8080`

### Response Structure

```json
{
  "message": "Operation successful.",
  "success": true,
  "data": { }
}
```
---
=======
# HMRS-App
Java Human Resource Management System
