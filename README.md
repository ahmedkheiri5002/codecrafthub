# CodeCraftHub

CodeCraftHub is a beginner-friendly Java Spring Boot REST API that allows developers to keep track of courses they want to learn. Instead of using a database, the application stores all course information in a local JSON file (`courses.json`), making it an excellent project for learning the fundamentals of REST APIs, file handling, and JSON processing with Spring Boot.

---

## Features

* Create new learning courses
* View all saved courses
* View a specific course by ID
* Update existing courses
* Delete courses
* Automatically generates unique course IDs
* Automatically creates `courses.json` if it does not exist
* Stores data using Jackson JSON processing
* Validates required fields and course status
* Returns appropriate HTTP status codes and error messages

---

# Technologies Used

* Java 17
* Spring Boot
* Spring Web
* Jackson Databind
* Maven

---

# Project Structure

```text
src
└── main
    ├── java
    │   └── com.codecrafthub
    │       ├── CodeCraftHubApplication.java
    │       ├── controller
    │       │   └── CourseController.java
    │       ├── model
    │       │   └── Course.java
    │       └── service
    │           └── CourseService.java
    └── resources
```

---

# Installation

## Prerequisites

* Java 17 or newer
* Maven 3.8+
* Git (optional)

## Clone the Repository

```bash
git clone https://github.com/yourusername/CodeCraftHub.git
```

or download the project as a ZIP file.

---

# Running the Application

## Using Maven

Navigate to the project directory and run:

```bash
mvn spring-boot:run
```

or

```bash
mvn clean install
java -jar target/codecrafthub-0.0.1-SNAPSHOT.jar
```

After the application starts, the API will be available at:

```text
http://localhost:8080
```

The JSON file (`courses.json`) will be created automatically in the project directory if it does not already exist.

---

# API Documentation

## Base URL

```text
http://localhost:8080/api
```

---

## Create a Course

**POST**

```text
/api/courses
```

Example Request

```json
{
  "name": "Spring Boot",
  "description": "Learn REST APIs",
  "target_date": "2026-08-15",
  "status": "Not Started"
}
```

Example Response

```json
{
  "success": true,
  "message": "Course added successfully"
}
```

---

## Get All Courses

**GET**

```text
/api/courses
```

Example Response

```json
{
  "success": true,
  "count": 2,
  "courses": [
    {
      "id": 1,
      "name": "Java",
      "description": "Learn Java Fundamentals",
      "target_date": "2026-08-01",
      "status": "Completed",
      "created_at": "2026-07-27T14:30:00"
    }
  ]
}
```

---

## Get a Course by ID

**GET**

```text
/api/courses/{id}
```

Example

```text
GET /api/courses/1
```

---

## Update a Course

**PUT**

```text
/api/courses/{id}
```

Example Request

```json
{
  "status": "Completed"
}
```

---

## Delete a Course

**DELETE**

```text
/api/courses/{id}
```

Example

```text
DELETE /api/courses/1
```

---

# Valid Status Values

The status field must be one of the following values exactly:

* Not Started
* In Progress
* Completed

Any other value will result in a **400 Bad Request** response.

---

# Error Handling

The application returns meaningful error messages for common issues, including:

* Missing required fields
* Invalid status values
* Course not found
* File read/write errors
* Invalid JSON requests

---

# Data Storage

All course information is stored in a local JSON file named:

```text
courses.json
```

If the file does not exist, it will be created automatically the first time the application runs.

---

# Testing the API

You can test the REST API using:

* Postman
* Insomnia
* curl
* Any REST client

Example:

```bash
curl http://localhost:8080/api/courses
```

---

# Troubleshooting

## Application will not start

* Verify that Java 17 or newer is installed.
* Ensure Maven is installed correctly.
* Confirm port **8080** is not already being used by another application.

---

## courses.json is not created

* Make sure the application has permission to write files in the project directory.
* Verify that the application started successfully.

---

## Invalid JSON errors

* Ensure all required fields are present.
* Verify that `target_date` uses the format:

```text
YYYY-MM-DD
```

* Ensure `status` is exactly one of:

  * Not Started
  * In Progress
  * Completed

---

## Course Not Found

If a requested course ID does not exist, the API returns a **404 Not Found** response.

---

# Future Improvements

Potential enhancements include:

* Database integration (MySQL or PostgreSQL)
* User authentication
* Search and filtering
* Pagination
* Course categories
* Unit and integration testing
* Swagger/OpenAPI documentation

---

# License

This project is intended for educational purposes as part of learning Java, Spring Boot, REST APIs, and JSON file handling.
