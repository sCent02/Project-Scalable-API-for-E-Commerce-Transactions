# 🛒 Scalable E-Commerce API Architecture

This project demonstrates a scalable E-Commerce API using **FastAPI, PostgreSQL, MongoDB, Redis, and AWS Deployment**.

## 📌 System Architecture

```mermaid
graph TD;
    A[Frontend (React/Vue)] -->|API Requests| B[FastAPI Backend];
    
    B -->|Stores User Data| C[PostgreSQL (Users, Orders)];
    B -->|Stores Product Data| D[MongoDB (Product Catalog)];
    B -->|Caches Products| E[Redis (Fast Caching)];

    C -->|Transaction Processing| F[Order Processing Service];
    F -->|Writes to PostgreSQL| C;
    F -->|Reads from MongoDB| D;

    B -->|Deployment| G[AWS (EC2, RDS, S3, Lambda)];

    classDef backend fill:#f9f,stroke:#333,stroke-width:2px;
    classDef database fill:#bbf,stroke:#333,stroke-width:2px;
    classDef cache fill:#ffb,stroke:#333,stroke-width:2px;
    classDef cloud fill:#faa,stroke:#333,stroke-width:2px;

    class B backend;
    class C database;
    class D database;
    class E cache;
    class G cloud;
