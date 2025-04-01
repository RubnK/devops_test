# RentACar - RESTful Car Lookup Application

**Author : [@RubnK](https://github.com/RubnK)**

RentACar is a lightweight Java Spring Boot web application exposing a REST API to retrieve cars based on their license plate. Built for clarity and simplicity, this project is containerized with Docker for easy deployment and portability.

## Table of Contents
- [Features](#features)
- [Technologies used](#technologies-used)
- [Project structure](#project-structure)
- [API Usage](#api-usage)
- [Installation & Execution](#installation--execution)
- [Run it locally](#run-it-locally)
- [Modify the car list](#modify-the-car-list)
- [License](#license)

## Features

- 🔍 **Plate-based car lookup**: Retrieve car information with a simple URL.
- 🚘 **Customizable car list**: Easily edit or expand the built-in dataset in `ServiceWeb.java`.
- ⚙️ **RESTful API**: Built with Spring Boot.
- 🐳 **Docker-ready**: Easily build and run using Docker.

---

## Technologies used

- Java 17
- Spring Boot 3
- Docker
- Maven/Gradle (build system)

---

## Project structure
```
/RentACar
│── src/
│   └── main/
│       └── java/
│           └── com/rubnk/RentACar/
│               ├── Car.java                  # Car model (plate, brand, price)
│               ├── RentACarApplication.java  # Spring Boot main class
│               └── ServiceWeb.java           # REST controller with endpoints
│── build.gradle                              # Build configuration
│── Dockerfile                                # Container definition
│── README.md                                 # Documentation
```

---

## API Usage

**Base URL** (Docker) :  
`http://localhost:4000`

### ➤ Get car by plate number

**Request**
```
GET /cars/{plateNumber}
```

**Example**
```
GET http://localhost:4000/cars/AA11BB
```

**Response**
```json
{
  "plateNumber": "AA11BB",
  "brand": "ferrari",
  "price": 2000
}
```

---

## Installation & Execution

### 1. Clone the repository
```sh
git clone https://github.com/RubnK/RentACar.git
cd RentACar
```

### 2. Build the application
```sh
./gradlew build
```

### 3. Build the Docker image
```sh
docker build -t rubnk/rentacar:1.0 .
```

### 4. Run the Docker container
```sh
docker run -p 4000:8080 rubnk/rentacar:1.0
```

> The application will be available at `http://localhost:4000`

---

## Run it locally

- You can also run it locally without Docker via:
  ```sh
  ./gradlew bootRun
  ```
  Then access the app on `http://localhost:8080/cars/AA11BB`

## Modify the car list

To customize or extend the list of available cars, edit the `ServiceWeb.java` constructor:

```java
public ServiceWeb() {
    Car car = new Car("AA11BB", "ferrari", 2000);
    cars.add(car);
    // Add your own cars here
}
```
You can add as many cars as needed by following the same format. 

## License

This project is licensed under the [MIT License](LICENSE).
