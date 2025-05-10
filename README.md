# SPSHPAU Backend Repository (spshpau-backend)

## Description

This "super-repository" manages the collection of backend microservices for the SPSHPAU project. It utilizes Git submodules to include each individual service, allowing for centralized management while maintaining separate repositories for each microservice.

The backend ecosystem provides functionalities for user management, project collaboration, real-time chat, and more, all orchestrated via an API Gateway and configured through a centralized Config Server.

## Overview of Microservices

This repository contains the following backend services as Git submodules, typically located under the `services/` directory:

* **Config Server (`spshpau-config`)**:
    * Manages and provides centralized configuration for all other microservices.
    * Uses a native backend (classpath-based YAML files).
* **Discovery Server (`spshpau-discovery`)**:
    * Netflix Eureka server for service registration and discovery, enabling dynamic communication between microservices.
* **API Gateway (`spshpau-gateway`)**:
    * Single entry point for all client requests, routing them to the appropriate backend services.
* **User Service (`spshpau-userservice`)**:
    * Handles user authentication, profiles (artist/producer), skills, genres, and user interactions (connections, blocking).
* **Project Service (`spshpau-projectservice`)**:
    * Manages projects, tasks, milestones, budgets, and project-related files (with S3 integration).
* **Chat Service (`spshpau-chatservice`)**:
    * Facilitates real-time one-to-one chat functionalities using WebSockets, manages user presence, and message persistence (MongoDB).

For detailed information on each service, please refer to the `README.md` file within its respective submodule directory (e.g., `services/userservice/README.md`).

## Technologies Used (Ecosystem Overview)

The SPSHPAU backend leverages a common technology stack across its microservices:

* **Backend Framework**: Java 17, Spring Boot 3.x
* **Inter-service Communication**: REST APIs, Feign Clients, Service Discovery (Eureka)
* **Database**: PostgreSQL (for User and Project services), MongoDB (for Chat service)
* **Configuration**: Spring Cloud Config Server
* **Service Discovery**: Spring Cloud Netflix Eureka
* **API Gateway**: Spring Cloud Gateway
* **Security**: OAuth2 with JWT Bearer Tokens (integration with Keycloak expected)
* **Build & Dependency Management**: Apache Maven
* **File Storage**: AWS S3 (used by Project Service)
* **Containerization**: Docker (see `docker-compose.yml` for orchestration)

## Prerequisites for the Ecosystem

To run the entire SPSHPAU backend ecosystem, you'll generally need:

* Java Development Kit (JDK) 17 or higher
* Apache Maven 3.6.x or higher
* Docker and Docker Compose
* An accessible PostgreSQL instance
* An accessible MongoDB instance
* An accessible OAuth2 Identity Provider (like Keycloak) configured as expected by the services.
* AWS S3 bucket and credentials (for Project Service file operations).

(Refer to individual service READMEs for more specific prerequisites if running them standalone.)

## Getting Started with the Super-Repository

### Cloning

To clone this super-repository along with all its submodules, use the `--recurse-submodules` flag:

```bash
git clone --recurse-submodules <URL_OF_THIS_SUPER_REPOSITORY>
cd spshpau-backend-super
