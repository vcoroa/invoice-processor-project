# Invoice Processor

This is a **technical test project** designed to show a scalable
and resilient invoice processing system built with Quarkus. It
receives invoices via REST API, extracts key data from PDFs,
and stores PDFs in AWS S3 and data in DynamoDB, using RabbitMQ
for async processing. It handles up to 1,000 invoices/hour.

## Project Structure
- **backend/**: REST API and core logic with Quarkus, S3, and
  DynamoDB.
- **consumer/**: Async message consumer using RabbitMQ.
- **frontend/**: (Optional) Future web interface.

## Features
- Receives invoice PDFs via a REST endpoint.
- Extracts data (installation number, address, items, dates,
  total) with Apache PDFBox.
- Stores PDFs in S3 and metadata in DynamoDB.
- Processes invoices asynchronously with RabbitMQ.
- Built for scalability, supporting 1,000 invoices/hour.

## Purpose
This is a practice exercise to show skills in building modern,
cloud-native apps with Quarkus, AWS, and message-driven design.
It’s based on a test from a Reddit post: [r/brdev - Recebi um
desafio técnico meio estranho](https://www.reddit.com/r/brdev/comments/1ix27ez/recebi_um_desafio_t%C3%A9cnico_meio_estranho/).

## Setup
1. Install Java 21, Maven, and Docker.
2. Configure AWS credentials in
   `backend/src/main/resources/application.properties`.
3. Start RabbitMQ: `docker run -d -p 5672:5672 rabbitmq:3-management`.
4. Run backend: `cd backend && mvn quarkus:dev`.
5. Test ping: `curl http://localhost:8080/ping` (returns "pong").

## Technical Details
- **Framework**: Quarkus (RESTEasy Reactive)
- **Messaging**: RabbitMQ with SmallRye Reactive Messaging
- **Storage**: AWS S3 (PDFs), DynamoDB (json data persistence)
- **PDF Processing**: Apache PDFBox
- **Frontend**: Angular 19
