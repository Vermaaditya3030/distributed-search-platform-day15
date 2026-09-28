# Day 15 — Distributed Search Platform

A portfolio-grade Java/Spring Boot project showing a simple distributed search architecture.

## Stack
- Java 17 + Spring Boot 3.3.5
- PostgreSQL 16
- REST microservices
- Docker Compose
- Spring Data JPA
- Actuator metrics

## Architecture
Client -> Ingest Service (8082) -> Search Service (8081) -> PostgreSQL

Search Service provides title/content search with a PostgreSQL query. Ingest Service forwards documents to the search service, giving you a clean separation between ingestion and query workloads.

## Run
```bash
docker compose up --build
```

## Add document
```bash
curl -X POST http://localhost:8082/api/ingest -H "Content-Type: application/json" -d '{"title":"Java Microservices","content":"Spring Boot Kafka Redis Docker"}'
```

## Search
```bash
curl "http://localhost:8081/api/documents?q=Kafka"
```

## Tests
```bash
mvn test
```

## GitHub
```bash
git init
git add .
git commit -m "Day 15 distributed search platform"
git branch -M main
git remote add origin https://github.com/Vermaaditya3030/distributed-search-platform-day15.git
git push -u origin main
```

## Production roadmap
Replace PostgreSQL LIKE search with OpenSearch/Elasticsearch; add Kafka-based indexing, Redis caching, pagination, ranking, typo tolerance, JWT/RBAC, rate limiting, tracing, dashboards, and horizontal replicas.
