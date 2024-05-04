This is a simple Go application that demonstrates the usage of Kafka for asynchronous communication between microservices. The application allows creating and listing products using HTTP endpoints and consumes messages from a Kafka topic to create products asynchronously.

Features
HTTP Server: Handles HTTP requests to create and list products.
MySQL Database: Stores product data persistently.
Kafka Integration: Consumes messages from a Kafka topic to create products asynchronously.

Prerequisites
Go installed on your machine (installation instructions)
Docker installed on your machine (installation instructions)
MySQL server running with the database products available at host.docker.internal:3306.
Kafka broker running at host.docker.internal:9094.
librdkafka-dev installed in the Docker container.

Installation
Clone the repository:
bash

Copy code
git clone https://github.com/your-username/go-kafka-product-service.git

Build the Docker image:
bash
Copy code
docker build -t go-kafka-product-service .
Run the Docker container:
bash
Copy code
docker run -d --name go-kafka-product-service go-kafka-product-service
Usage

The application exposes the following HTTP endpoints:

POST /products: Create a new product. Send a JSON payload with the product name and price.
GET /products: Retrieve a list of all products.
Configuration

Ensure the following environment variables are set:

MYSQL_DSN: MySQL data source name (root:root@tcp(host.docker.internal:3306/products)).
KAFKA_BROKERS: Comma-separated list of Kafka brokers (host.docker.internal:9094).
KAFKA_TOPICS: Comma-separated list of Kafka topics to consume (products).

License
This project is licensed under the MIT License - see the LICENSE file for details.
