# log-monitoring-platform

## Problem Statement

Modern distributed systems generate massive volumes of logs across services and servers.
Debugging production issues becomes extremely difficult without centralized log collection, search, and alerting.

This project builds a **distributed log observability platform** that:

* Collects logs from multiple machines
* Streams them in real time
* Stores them efficiently
* Enables fast search
* Triggers alerts on anomalies

This simulates **real production-grade logging infrastructure** used in tech companies.

---

## What We Are Building

A system composed of the following components:

### 1. Log Agent

* Python service running on multiple machines
* Reads system/application logs
* Sends logs to Kafka
* Handles:

  * batching
  * retries
  * backpressure

---

### 2. Streaming Layer

* Kafka running in Docker
* Topics with multiple partitions
* Ensures:

  * durability
  * scalability
  * parallel consumption using consumer groups

---

### 3. Ingest Service

* Built using FastAPI
* Consumes logs from Kafka
* Validates log schema
* Adds metadata:

  * hostname
  * timestamp
  * log level
* Pushes processed logs to storage

---

### 4. Storage Layer

* PostgreSQL → stores metadata
* ElasticSearch → full-text log search
* Optimized indexing for performance

---

### 5. Alerting Engine

* Rule-based alerts:

  * ERROR spikes
  * latency anomalies
* Sends notifications via:

  * email (initially)

---

### 6. API Layer

* REST APIs to:

  * search logs
  * fetch statistics
  * manage alerts
* Security:

  * JWT authentication
  * rate limiting

---

### 7. Dashboard & Observability

* Basic UI dashboard showing:

  * log volume
  * error rate
  * active alerts
* Observability stack:

  * Prometheus
  * Grafana
  * Alertmanager

---

### 8. DevOps

* Docker for all services
* Docker-compose for orchestration
* CI/CD pipeline:

  * run tests
  * build images
  * deploy automatically

---

### 9. Kubernetes (Advanced Phase)

* Local Kubernetes using Kind
* Features:

  * auto scaling
  * rolling updates
  * crash recovery testing

---

## Tech Stack

* Python (FastAPI)
* Kafka
* PostgreSQL
* ElasticSearch
* Redis
* Docker
* GitHub Actions
* Prometheus + Grafana
* Kubernetes (Kind)

---

## Non-Functional Requirements

* Handle 10,000 logs/sec
* Zero message loss
* Horizontal scalability
* Secure APIs
* Observability-first design
* Cost-efficient architecture

---

## Failure Scenarios to Test

* Kafka broker crash
* Service pod killed
* Database connection loss
* Traffic spike
* Disk full
