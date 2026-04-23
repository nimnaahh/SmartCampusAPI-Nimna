# SmartCampusAPI-Nimna


## Project Overview
The **Smart Campus API** is a RESTful web service designed to manage campus infrastructure, specifically focusing on **Rooms**, **Sensors**, and **Sensor Readings**. This project was developed as part of the coursework for the BSc (Hons) Computer Science program.

The system allows administrators to track room statuses, manage various types of sensors (e.g., Temperature, Humidity, Occupancy), and record historical data points for analysis.

## Key Features
- **Room Management**: Create, view, and delete campus rooms.
- **Sensor Integration**: Deploy sensors within specific rooms and track their operational status.
- **Data Logging**: Record and retrieve time-stamped readings from deployed sensors.
- **Resource Discovery**: A root discovery endpoint providing API documentation and versioning.
- **Robust Error Handling**: Custom exception mappers for consistent error responses (e.g., preventing room deletion if sensors are attached).
- **Request Logging**: Automated logging of incoming requests for monitoring and debugging.

---

## Technical Stack
- **Language**: Java 17
- **Framework**: Jakarta EE 8 / JAX-RS (Jersey)
- **Dependency Management**: Maven
- **JSON Processing**: Jackson
- **Storage**: In-memory Data Store (Thread-safe Concurrent Maps)
- **Deployment**: WAR (Web Archive) for Jakarta-compatible servers (e.g., Payara, Glassfish, Tomcat)

---

## API Endpoints

### 1. Discovery
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | API Information and resource map |

### 2. Rooms
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/v1/rooms` | Retrieve all rooms |
| `POST` | `/api/v1/rooms` | Create a new room |
| `GET` | `/api/v1/rooms/{id}` | Get specific room details |
| `DELETE` | `/api/v1/rooms/{id}`| Delete a room (fails if sensors exist) |

### 3. Sensors
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/v1/sensors` | List all sensors (supports filtering by `type`) |
| `POST` | `/api/v1/sensors` | Register a new sensor |
| `GET` | `/api/v1/sensors/{id}`| Get specific sensor details |

### 4. Sensor Readings
| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/api/v1/sensors/{id}/readings` | Get all readings for a sensor |
| `POST` | `/api/v1/sensors/{id}/readings` | Submit a new reading |

---

## Business Rules & Constraints
- **Referential Integrity**: A room cannot be deleted if it still has sensors assigned to it.
- **Consistency**: Sensor readings cannot be added to non-existent sensors.
- **Validation**: Basic validation on room and sensor names to ensure data quality.
- **Data Persistence**: As per project requirements, data is stored in-memory and will reset upon server restart.

---

## Setup and Execution

### Prerequisites
- JDK 17
- Apache Maven 3.6+
- A compatible Servlet Container (e.g., Apache Tomcat 9+ or Payara Server)

### Build
To compile the project and generate the WAR file:
```bash
mvn clean package
```
The resulting `SmartCampusAPI.war` will be located in the `target/` directory.

### Running Locally
1. Deploy the generated `.war` file to your preferred application server.
2. Access the API at: `http://localhost:8080/SmartCampusAPI/` (Context path may vary based on server configuration).

---
## Author
- **Name**: Nimna
- **Student ID**: w2120456

