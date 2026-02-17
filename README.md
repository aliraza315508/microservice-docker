Spring Boot Microservices with Docker

This project demonstrates a containerized microservices architecture built using Spring Boot and Spring Cloud. The system follows real-world microservice design principles including service discovery, API gateway routing, and distributed tracing. All services run inside Docker containers and communicate through Eureka.

Technology Stack

This project is built using:

Java 17

Spring Boot 3

Spring Cloud (Eureka and Gateway)

Docker and Docker Compose

Zipkin for distributed tracing

Maven

Services Overview

The system consists of the following services:

Naming Server
Provides service discovery using Eureka.
Runs on port 8761.

API Gateway
Handles routing and acts as a single entry point to the system.
Runs on port 8765.

Currency Exchange Service
Provides exchange rate data between currencies.
Runs on port 8000.

Currency Conversion Service
Uses the exchange service to calculate currency conversion.
Runs on port 8100.

Zipkin Server
Collects and visualizes distributed tracing data.
Runs on port 9411.

All services register themselves with Eureka and communicate using service names instead of hardcoded URLs.

Project Structure

The root directory contains the docker-compose file and individual folders for each microservice.
Each microservice is an independent Spring Boot application with its own Maven configuration.

The structure includes:

naming-server

api-gateway

currency-exchange-service

currency-conversion-service

docker-compose.yml

README.md

Prerequisites

Before running the project, make sure you have:

Java 17 or higher
Maven 3.8 or higher
Docker Desktop installed and running

Building the Docker Images

Each service is packaged into a Docker image using Spring Boot buildpacks.
To build the images, navigate into each service directory and run Maven with the Spring Boot image build goal.

Repeat this process for all four services.

You can confirm the images are created successfully by checking Docker images locally.

Running the System

From the project root directory, start all services using Docker Compose.

Once started, the services will automatically register with Eureka and become discoverable.

You can stop all services using Docker Compose when finished.

Accessing the Applications

Eureka Dashboard
Open your browser and navigate to localhost on port 8761 to see all registered services.

Zipkin Dashboard
Open localhost on port 9411 to view distributed traces.

API Gateway
The gateway runs on port 8765 and acts as the main entry point for all requests.

You can test the currency conversion flow by calling the conversion endpoint through the gateway.

Observability

Each service includes Spring Boot Actuator and is configured for distributed tracing.
Tracing data is sent to Zipkin for visualization.

Sampling probability can be adjusted in the application configuration depending on how much tracing is required.
