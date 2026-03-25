# 💳 Cash Card API

A secure RESTful API for managing family cash cards, built with Spring Boot as part of
the [Spring Academy - Building a REST API](https://spring.academy/courses/building-a-rest-api-with-spring-boot) course.

## ✨ Features

- **Complete CRUD Operations** - Create, read, update, and delete cash cards
- **Secure Authentication** - HTTP Basic authentication with BCrypt password hashing
- **Owner-Based Access Control** - Users can only access and modify their own cash cards
- **Pagination & Sorting** - Efficient handling of large datasets
- **RESTful Design** - Follows REST conventions and best practices

## 🚀 Getting Started

### Prerequisites

- Java 21 or higher
- Gradle (or use included wrapper)

### Running the Application

```bash
# Using Gradle wrapper (recommended)
./gradlew bootRun

# Or if you have Gradle installed
gradle bootRun
```

The API will be available at `http://localhost:8080`

### Running Tests

```bash
./gradlew test
```

## 📚 API Endpoints

| Method   | Endpoint          | Description                     |
|----------|-------------------|---------------------------------|
| `GET`    | `/cashcards`      | List all cash cards (paginated) |
| `GET`    | `/cashcards/{id}` | Get a specific cash card        |
| `POST`   | `/cashcards`      | Create a new cash card          |
| `PUT`    | `/cashcards/{id}` | Update a cash card              |
| `DELETE` | `/cashcards/{id}` | Delete a cash card              |

### Example Request

```bash
# Get all cash cards
curl -u sarah:abc123 http://localhost:8080/cashcards

# Create a new cash card
curl -X POST -u sarah:abc123 \
  -H "Content-Type: application/json" \
  -d '{"amount": 123.45}' \
  http://localhost:8080/cashcards
```

## 🔐 Authentication

The API uses HTTP Basic authentication. Test users:

| Username | Password | Role       |
|----------|----------|------------|
| sarah    | abc123   | CARD-OWNER |
| hank     | qrs456   | NON-OWNER  |
| kumar    | xyz789   | CARD-OWNER |

## 🛠️ Tech Stack

- **Spring Boot 3.5.11** - Application framework
- **Spring Data JDBC** - Database access
- **Spring Security** - Authentication and authorization
- **H2 Database** - In-memory database for development
- **JUnit 5** - Testing framework
- **Gradle** - Build tool

## 📁 Project Structure

```
cashcard/
├── src/
│   ├── main/
│   │   ├── java/example/cashcard/
│   │   │   ├── CashCard.java           # Domain model
│   │   │   ├── CashCardController.java # REST controller
│   │   │   ├── CashCardRepository.java # Data repository
│   │   │   └── SecurityConfig.java     # Security configuration
│   │   └── resources/
│   │       ├── schema.sql              # Database schema
│   │       └── data.sql                # Test data
│   └── test/
│       └── java/example/cashcard/
│           └── CashCardApplicationTests.java
├── build.gradle
└── README.md
```

## 🧪 Testing

The project includes comprehensive integration tests covering:

- JSON serialization/deserialization
- CRUD operations
- Authentication and authorization
- Pagination and sorting
- Ownership validation

## 📝 License

This project is created for educational purposes as part of the Spring Academy course.
