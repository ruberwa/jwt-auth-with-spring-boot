# JWT Auth with Spring Boot

A Spring Boot project implementing JWT (JSON Web Token) authentication for securing RESTful APIs. This application allows user registration, login, and access control to protected resources.

## Features

- User registration and login
- JWT token generation and validation
- Secure access to API endpoints
- Spring Security integration
- Role-based access control (optional)

## Technologies Used

- Spring Boot
- Spring Security
- MySQL Database
- Maven (for project management)

## Getting Started

### Prerequisites

- Java 17 or higher
- MySQL database server
- Maven (for building the project)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ruberwa/jwt-auth-with-spring-boot.git
   ```

2. Navigate to the project directory:
   ```bash
   cd jwt-auth-with-spring-boot
   ```

3. Configure your MySQL database:
   - Create a database for the project.

4. Update the `src/main/resources/application.properties` file with your database connection details:
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/your_database_name
   spring.datasource.username=your_username
   spring.datasource.password=your_password
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   ```

5. Build the project:
   ```bash
   mvn clean install
   ```

6. Run the application:
   ```bash
   mvn spring-boot:run
   ```

## API Endpoints

- **POST** `/api/auth/register`: Register a new user
- **POST** `/api/auth/login`: Authenticate a user and receive a JWT
- **GET** `/api/protected`: Access a protected resource (authentication required)

## Example Usage

Use tools like Postman or curl to interact with the API. Include the JWT token in the Authorization header for protected routes:
```
Authorization: Bearer <your_jwt_token>
```

### Sample Registration Request

#### **POST** `/api/auth/register`
- **Content-Type:** `application/json`

```json
{
  "names": "Example User",
  "email": "example@example.com",
  "phoneNumber": "1234567890",
  "password": "examplePassword"
}
```

### Sample Login Request

#### **POST** `/api/auth/login`
- **Content-Type:** `application/json`

```json
{
  "email": "example@example.com",
  "password": "examplePassword"
}
```

### Contributing

Contributions are welcome! Please open an issue or submit a pull request for any improvements or features you'd like to add.

### Customization

- Replace `your_database_name`, `your_username`, and `your_password` in the configuration section with your actual details.
- Feel free to adjust the API endpoints and any example requests based on your implementation.

