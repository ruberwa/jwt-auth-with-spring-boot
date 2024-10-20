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


# AM USING UBUNTU - How to Create a MySQL Database on Ubuntu

This guide provides step-by-step instructions for creating a MySQL database and user on Ubuntu.

## Step 1: Install MySQL (if not already installed)

If you haven't installed MySQL yet, you can do so by running:

```bash
sudo apt update
sudo apt install mysql-server
```

## Step 2: Start MySQL Service

Ensure that the MySQL service is running:

```bash
sudo service mysql start
```

## Step 3: Log in to MySQL

Log in to the MySQL shell with the root user:

```bash
sudo mysql -u root -p
```

You will be prompted to enter the root password you set during MySQL installation.

## Step 4: Create the Database

Once you are in the MySQL shell, you can create your database with the following commands:

1. **Create the database**:

   ```sql
   CREATE DATABASE jwt_spring_auth_db;
   ```

2. **Create the user** (replace `your_username` and `your_password` with your desired username and password):

   ```sql
   CREATE USER 'jwt_spring_auth_user'@'localhost' IDENTIFIED BY 'jwt_spring_auth_pass';
   ```

3. **Grant permissions to the user**:

   ```sql
   GRANT ALL PRIVILEGES ON jwt_spring_auth_db.* TO 'jwt_spring_auth_user'@'localhost';
   ```

4. **Flush the privileges** to ensure that the changes take effect:

   ```sql
   FLUSH PRIVILEGES;
   ```

5. **Exit the MySQL shell**:

   ```sql
   EXIT;
   ```

## Summary of Commands

Here's a summary of the commands you will run in the MySQL shell:

```sql
CREATE DATABASE jwt_spring_auth_db;
CREATE USER 'jwt_spring_auth_user'@'localhost' IDENTIFIED BY 'Jwt_Spring_Auth_2024';
GRANT ALL PRIVILEGES ON jwt_spring_auth_db.* TO 'jwt_spring_auth_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

## Step 5: Update Your Application Properties

Now that you've created the database and user, update your `application.properties` file with the new credentials:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/jwt_spring_auth_db
spring.datasource.username=jwt_spring_auth_user
spring.datasource.password=Jwt_Spring_Auth_2024
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```

## Final Step

After updating the properties, you can build and run your Spring Boot application, and it should connect to the MySQL database you just created.
