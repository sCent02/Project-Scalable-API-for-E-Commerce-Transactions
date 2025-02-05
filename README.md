# 🛒 Scalable E-Commerce API Architecture

This project demonstrates a scalable E-Commerce API using **FastAPI, PostgreSQL, MongoDB, Redis, and AWS Deployment**.

## 📌 System Architecture

```mermaid
graph TD;
    Frontend[Frontend (React/Vue)] -->|API Requests| FastAPI[FastAPI Backend]
    
    FastAPI -->|Stores User Data| PostgreSQL[PostgreSQL (Users, Orders)]
    FastAPI -->|Stores Product Data| MongoDB[MongoDB (Product Catalog)]
    FastAPI -->|Caches Products| Redis[Redis (Fast Caching)]

    PostgreSQL -->|Transaction Processing| Orders[Order Processing Service]
    Orders -->|Writes to PostgreSQL| PostgreSQL
    Orders -->|Reads from MongoDB| MongoDB

    FastAPI -->|Deployment| AWS[EC2, RDS, S3, Lambda]

    style FastAPI fill:#f9f,stroke:#333,stroke-width:2px;
    style PostgreSQL fill:#bbf,stroke:#333,stroke-width:2px;
    style MongoDB fill:#bfb,stroke:#333,stroke-width:2px;
    style Redis fill:#ffb,stroke:#333,stroke-width:2px;
    style AWS fill:#faa,stroke:#333,stroke-width:2px;
