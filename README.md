# Eureka Server - Microservices Service Registry

This repository contains the Eureka Server setup for a Spring Boot microservices architecture.
Eureka Server provides service discovery, allowing microservices to register themselves and locate other services by name instead of relying on hardcoded IP addresses or hostnames.

---

## Features

* Acts as a centralized Service Registry for microservices.
* Services automatically register and send periodic heartbeats to notify availability.
* Automatically removes inactive services if no heartbeat is received.
* Provides a web dashboard at `http://localhost:8761`.

---

## Project Structure

```
microservices-system/
│── pom.xml                # Parent pom (aggregator)
│── eureka-server/         # Eureka Server module
    │── src/main/java/...  # Application source code
    │── src/main/resources/application.properties
```

---

## Configuration

**application.properties**

```properties
spring.application.name=eureka-server
server.port=8761

# Disable self-registration as a client
eureka.client.register-with-eureka=false
eureka.client.fetch-registry=false
```

**Main Application**

```java
@SpringBootApplication
@EnableEurekaServer
public class SpringEurekaServerApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringEurekaServerApplication.class, args);
    }
}
```

---

## How to Run

1. Clone the repository:

   ```bash
   git clone https://github.com/<your-username>/eureka-server.git
   cd microservices-system/eureka-server
   ```

2. Build the project:

   ```bash
   mvn clean install
   ```

3. Start the Eureka Server:

   ```bash
   mvn spring-boot:run
   ```

4. Access the Eureka Dashboard:

   ```
   http://localhost:8761
   ```

---

## Technology Stack

* Java 17
* Spring Boot 3.0.6
* Spring Cloud Netflix Eureka
* Maven

---

## Next Steps

* Add additional microservices (e.g., `auth-service`, `image-service`, `gallery-service`) and register them with Eureka.
* Use service discovery instead of hardcoded service locations.
* Integrate with an API Gateway (e.g., Spring Cloud Gateway) for routing and load balancing.

---

## License

This project is licensed under the MIT License.
