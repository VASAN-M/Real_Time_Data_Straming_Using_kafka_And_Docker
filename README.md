# Apache Kafka and Zookeeper Setup Using Docker Compose

This project provides a lightweight and production-aligned **Docker Compose**
configuration for running **Apache Kafka** and **Apache Zookeeper** locally.
It is designed for learning Kafka fundamentals, testing producers and consumers,
and creating a reliable local development environment.

---

## Overview

Apache Kafka relies on Zookeeper for broker coordination and metadata
management. This setup uses official **Confluent Platform Docker images**
to deploy a single Kafka broker along with Zookeeper in isolated containers.

The configuration exposes the necessary ports to support both:
- Inter-container communication
- Local host access for development and testing

---

## Services

### Zookeeper
- **Image:** `confluentinc/cp-zookeeper:7.5.0`
- **Port:** `2181`
- **Purpose:**  
  Handles Kafka broker coordination, configuration, and metadata management.

---

### Kafka
- **Image:** `confluentinc/cp-kafka:7.5.0`
- **Ports:**
  - `9092` – Internal Docker network communication
  - `29092` – Local host access
- **Configuration:**
  - Single broker setup
  - Advertised listeners configured for both internal and external access
- **Dependency:**  
  Requires Zookeeper to be running before startup

---

## Technology Stack
- Docker
- Docker Compose
- Apache Kafka
- Apache Zookeeper
- Confluent Platform Docker Images

---

## Docker Compose Configuration Highlights
- Single-node Kafka broker suitable for local development
- Zookeeper exposed on port `2181`
- Kafka advertised listeners configured for:
  - Container-to-container communication
  - Local machine access
- Clean separation of services using Docker Compose

---

## Prerequisites
Ensure the following are installed on your system:
- Docker
- Docker Compose

---

## Getting Started

### 1. Clone the Repository
```bash
git clone <repository-url>
cd <project-directory>
docker-compose up -d
docker ps
