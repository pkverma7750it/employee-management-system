# 🏢 Employee Management System

[![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://openjdk.org/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.1.5-brightgreen.svg)](https://spring.io/projects/spring-boot)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](http://makeapullrequest.com)

> A production-ready Employee Management System with REST API and modern web interface. Built with Spring Boot, JPA/Hibernate, and vanilla JavaScript.

## ✨ Features

### Backend Features
- ✅ **Full CRUD Operations** - Create, Read, Update, Delete employees
- ✅ **RESTful API** - Well-structured REST endpoints with proper HTTP methods
- ✅ **Validation** - Input validation with meaningful error messages
- ✅ **Global Exception Handling** - Consistent error responses across all endpoints
- ✅ **Layered Architecture** - Controller → Service → Repository pattern
- ✅ **H2 Database** - In-memory database for development (easy to switch to PostgreSQL/MySQL)
- ✅ **JPA/Hibernate** - Object-relational mapping with automatic schema generation
- ✅ **Department Analytics** - Group by department, average salary calculations
- ✅ **Years of Service** - Automatic calculation based on joining date

### Frontend Features
- ✅ **Responsive Design** - Works on desktop, tablet, and mobile
- ✅ **Real-time Search** - Filter employees by name, department, email, or salary
- ✅ **Interactive UI** - Add, edit, delete, and view employee details
- ✅ **Live Statistics** - Real-time total employee count and average salary
- ✅ **Modern CSS** - Gradient backgrounds, smooth animations, card-based layout
- ✅ **No Frameworks** - Pure HTML/CSS/JS - no build steps required
- ✅ **Auto-refresh** - Dashboard updates every 10 seconds

## 🚀 Quick Start

### Prerequisites

- Java 17 or higher
- Maven (or use the included Maven wrapper)
- Your favorite IDE (IntelliJ, VS Code, Eclipse)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/employee-management-system.git
   cd employee-management-system
Build the application

bash
mvn clean package
Run the application

bash
mvn spring-boot:run
Open your browser

text
http://localhost:8080
The application will start with sample data pre-loaded!

📚 API Documentation
Base URL
text
http://localhost:8080/api/employees
Endpoints
Method	Endpoint	Description	Request Body	Response
GET	/	Get all employees	-	200 OK + Array of employees
GET	/{id}	Get employee by ID	-	200 OK + Employee object
POST	/	Create new employee	Employee JSON	201 CREATED + Created employee
PUT	/{id}	Update employee	Employee JSON	200 OK + Updated employee
DELETE	/{id}	Delete employee	-	204 NO CONTENT
GET	/department/{dept}	Get employees by department	-	200 OK + Filtered array
GET	/reports/average-salary	Get average salary	-	200 OK + {"averageSalary": 81000}
GET	/reports/group-by-department	Group employees by department	-	200 OK + Grouped Map
Example API Calls
Create Employee
bash
curl -X POST http://localhost:8080/api/employees \
  -H "Content-Type: application/json" \
  -d '{
    "name": "John Doe",
    "department": "Engineering",
    "salary": 90000,
    "email": "john.doe@company.com",
    "joiningDate": "2023-01-15"
  }'
Get All Employees
bash
curl http://localhost:8080/api/employees
Update Employee
bash
curl -X PUT http://localhost:8080/api/employees/1 \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Alice Johnson",
    "department": "Engineering",
    "salary": 105000,
    "email": "alice.johnson@company.com",
    "joiningDate": "2020-01-15"
  }'
Delete Employee
bash
curl -X DELETE http://localhost:8080/api/employees/5
Get Engineering Department
bash
curl http://localhost:8080/api/employees/department/Engineering
Get Analytics
bash
# Average salary
curl http://localhost:8080/api/employees/reports/average-salary

# Group by department
curl http://localhost:8080/api/employees/reports/group-by-department
🏗️ Architecture
text
┌─────────────────────────────────────────────┐
│            Browser / API Client             │
└─────────────────┬───────────────────────────┘
                  │ HTTP/REST
                  ↓
┌─────────────────────────────────────────────┐
│         Spring Boot Application             │
│  ┌─────────────────────────────────────┐    │
│  │   Controller Layer (@RestController) │    │
│  │   - Request mapping                  │    │
│  │   - Validation                       │    │
│  │   - Response handling                │    │
│  └─────────────────────────────────────┘    │
│                  ↓                           │
│  ┌─────────────────────────────────────┐    │
│  │   Service Layer (@Service)          │    │
│  │   - Business logic                  │    │
│  │   - Transaction management          │    │
│  └─────────────────────────────────────┘    │
│                  ↓                           │
│  ┌─────────────────────────────────────┐    │
│  │   Repository Layer (@Repository)    │    │
│  │   - Data access                     │    │
│  │   - JPA operations                  │    │
│  └─────────────────────────────────────┘    │
└─────────────────┬───────────────────────────┘
                  │ JDBC/JPA
                  ↓
┌─────────────────────────────────────────────┐
│           H2 Database (In-memory)           │
│            employees table                  │
└─────────────────────────────────────────────┘
📁 Project Structure
text
employee-management-system/
├── src/
│   ├── main/
│   │   ├── java/com/company/employeeapi/
│   │   │   ├── controller/
│   │   │   │   └── EmployeeController.java      # REST endpoints
│   │   │   ├── service/
│   │   │   │   └── EmployeeService.java         # Business logic
│   │   │   ├── repository/
│   │   │   │   └── EmployeeRepository.java      # JPA repository
│   │   │   ├── entity/
│   │   │   │   └── Employee.java                # JPA entity
│   │   │   ├── exception/
│   │   │   │   └── GlobalExceptionHandler.java  # Global error handling
│   │   │   ├── DataLoader.java                  # Sample data loader
│   │   │   └── EmployeeApiApplication.java      # Main class
│   │   └── resources/
│   │       ├── static/
│   │       │   └── index.html                   # Web interface
│   │       └── application.properties           # Configurations
│   └── test/                                    # Unit tests
├── pom.xml                                      # Maven dependencies
└── README.md                                    # This file
🛠️ Technology Stack
Backend
Technology	Version	Purpose
Java	17	Core language
Spring Boot	3.1.5	Application framework
Spring Data JPA	3.1.5	Database access
H2 Database	2.1.214	Development database
Maven	3.9+	Build tool
Hibernate	6.2+	ORM
Frontend
Technology	Purpose
HTML5	Structure
CSS3	Styling (Flexbox, Grid, Animations)
JavaScript (ES6)	Interactivity, Fetch API
No external frameworks	Pure vanilla JS for performance
📊 Database Schema
sql
CREATE TABLE employees (
    id BIGINT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    department VARCHAR(50) NOT NULL,
    salary DOUBLE NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE,
    joining_date DATE NOT NULL
);
🧪 Testing
Run Unit Tests
bash
mvn test
Manual API Testing with cURL
bash
# Create test script
./test-api.sh
🚢 Deployment
Deploy to Production
Build JAR file

bash
mvn clean package
Run JAR

bash
java -jar target/employee-api-0.0.1-SNAPSHOT.jar
Configure for Production

Change database to PostgreSQL/MySQL

Set up connection pooling

Enable production logging

Configure CORS for frontend

Docker Deployment
dockerfile
FROM openjdk:17-jdk-slim
COPY target/employee-api-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "/app.jar"]
bash
docker build -t employee-system .
docker run -p 8080:8080 employee-system
🎯 Future Enhancements
JWT Authentication & Authorization

PostgreSQL/MySQL support

Export to CSV/Excel

Salary charts and graphs

Department-wise analytics dashboard

Email notifications

Unit & Integration tests

Swagger/OpenAPI documentation

CI/CD pipeline with GitHub Actions

Kubernetes deployment

Redis caching

Microservices architecture

🤝 Contributing
Contributions are welcome! Please feel free to submit a Pull Request.

Fork the repository

Create your feature branch (git checkout -b feature/AmazingFeature)

Commit your changes (git commit -m 'Add some AmazingFeature')

Push to the branch (git push origin feature/AmazingFeature)

Open a Pull Request

📝 License
This project is licensed under the MIT License - see the LICENSE file for details.

👨‍💻 Author
PAWAN KUMAR

GitHub: @pkverma7750it

LinkedIn: linkedin.com/in/pawan-kumar-942979404

Portfolio: linkedin.com/in/pawan-kumar-942979404

🙏 Acknowledgments
Spring Boot team for the amazing framework

Baeldung for excellent Spring tutorials

H2 Database for perfect development database

All contributors and users of this project

📧 Contact
For questions or feedback, please open an issue or email: pkverma7750it@gmail.com

⭐ Show Your Support
If this project helped you, please give it a ⭐ on GitHub!
