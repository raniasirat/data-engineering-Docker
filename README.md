# 🐳 Data Engineering Pipeline with Docker & PostgreSQL

![Docker](https://img.shields.io/badge/Docker-Containerized-blue)
![Python](https://img.shields.io/badge/Python-3.13-yellow)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

##  Overview

This project showcases a **modern data engineering pipeline** built with Docker.
It demonstrates how to **ingest, process, and store data at scale** using containerized workflows.

 Built as part of a **Data Engineering learning journey**, this project focuses on:

* Reproducibility
* Scalability
* Clean architecture

---

##  What This Project Does

✔️ Downloads real-world dataset (NYC Taxi data)
✔️ Processes data using **pandas**
✔️ Loads data into **PostgreSQL**
✔️ Runs everything inside **Docker containers**
✔️ Uses **chunk processing** for large datasets

---

##  Architecture

```
        ┌──────────────┐
        │   CSV Data   │
        │ (NY Taxi)    │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │   Python     │
        │  (pandas)    │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │ PostgreSQL   │
        │  Database    │
        └──────┬───────┘
               │
               ▼
        ┌──────────────┐
        │  pgAdmin UI  │
        └──────────────┘
```

---

##  Tech Stack

| Category         | Tools           |
| ---------------- | --------------- |
| Language         | Python 3.13     |
| Data Processing  | pandas          |
| Database         | PostgreSQL      |
| Containerization | Docker          |
| Orchestration    | Docker Compose  |
| Package Manager  | uv              |
| DB Interface     | pgAdmin / pgcli |

---

## 📂 Project Structure

```
.
├── pipeline/
│   ├── pipeline.py          # simple pipeline example
│   ├── ingest_data.py       # full ingestion pipeline
│   ├── pyproject.toml
│   ├── uv.lock
│
├── test/                    # volume testing folder
│
├── Dockerfile
├── docker-compose.yaml
└── .gitignore
```

---

##  Quick Start

### 1️⃣ Clone the repo

```bash
git clone https://github.com/your-username/your-repo.git
cd data-engineering-Docker
```

---

### 2️⃣ Start services

```bash
docker-compose up -d
```

🔗 Access:

* PostgreSQL → `localhost:5432`
* pgAdmin → http://localhost:8085

---

### 3️⃣ Run pipeline locally

```bash
uv run python pipeline.py 10
```

📁 Output:

```
output_day_10.parquet
```

---

### 4️ Run ingestion pipeline

```bash
uv run python ingest_data.py \
  --pg-user=root \
  --pg-pass=root \
  --pg-host=localhost \
  --pg-port=5432 \
  --pg-db=ny_taxi \
  --target-table=yellow_taxi_trips \
  --year=2021 \
  --month=1
```

---

##  Docker Usage

### Build image

```bash
docker build -t taxi_pipeline .
```

### Run container

```bash
docker run -it taxi_pipeline 10
```

---

##  Example SQL Queries

```sql
-- Total rows
SELECT COUNT(*) FROM yellow_taxi_trips;

-- Trips per day
SELECT 
    DATE(tpep_pickup_datetime) AS date,
    COUNT(*) AS trips
FROM yellow_taxi_trips
GROUP BY date
ORDER BY date;
```

---

##  Key Features

✨ Fully containerized workflow
✨ Reproducible environments
✨ Handles large datasets (chunking)
✨ Clean separation of concerns
✨ Scalable design

---

## Important Notes

* Docker containers are **stateless**
* Use volumes to persist PostgreSQL data
* `.parquet` files are ignored via `.gitignore`

---

##  Cleanup

```bash
docker-compose down
docker system prune -a --volumes
```

---

##  Learning Outcomes

✔️ Docker fundamentals
✔️ Data pipeline design
✔️ PostgreSQL integration
✔️ Handling large datasets efficiently
✔️ Real-world data engineering workflow

---

## Screenshot
* pgAdmin dashboard
<img width="1367" height="1059" alt="image" src="https://github.com/user-attachments/assets/1d6ad66a-f9f8-47a3-a8b3-8b539a755d1d" />
---

##  Author

**Rania Sirat**

---
