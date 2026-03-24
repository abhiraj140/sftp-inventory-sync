# 📦 sftp-inventory-sync

## 🚀 Overview
**sftp-inventory-sync** is a high-performance MuleSoft application designed to process large-scale CSV data efficiently under constrained resources.

The application reads a CSV file (up to 1GB) from a source SFTP location, processes the data by grouping records based on `storeId`, and generates multiple output CSV files—each corresponding to a unique `storeId`. These output files are then written to a target SFTP location.

This solution is optimized to run within strict infrastructure limits (0.2 vCores) while ensuring the entire processing completes within a 30-minute execution window. The job is scheduled to run once daily.

---

## 🎯 Key Objectives
- Process large CSV files (up to 1GB) efficiently
- Segregate records dynamically based on `storeId`
- Generate multiple output files (one per unique `storeId`)
- Ensure completion within **30 minutes**
- Operate within **0.2 vCore resource constraints**
- Execute as a **daily scheduled job**

---

## 🏗️ Architecture & Design

### 📥 Input
- Source: SFTP server
- File type: CSV (up to 1GB)

### ⚙️ Processing Logic
- Stream-based file processing to handle large payloads
- Dynamic segregation of records using `storeId`
- Parallel and batch processing for optimized throughput

### 📤 Output
- Multiple CSV files generated dynamically
- Each file contains records belonging to a single `storeId`
- Files written to target SFTP location

---

## ⚡ Performance Optimization

To meet strict resource and time constraints, the application leverages:

- **Streaming Processing**
  - Avoids loading the entire file into memory
  - Prevents OutOfMemory errors

- **Batch Processing**
  - Efficient handling of large datasets in chunks

- **Parallel Processing**
  - Improves throughput while staying within CPU limits

- **Dynamic Routing**
  - Routes records to appropriate output streams based on `storeId`

- **Circuit Breaker Pattern**
  - Prevents resource exhaustion during failures

---

## 🔄 Error Handling & Resilience

The application is designed with robust error-handling strategies:

- **Retry Mechanism**
  - Automatic retries for transient errors

- **Persistent Error Handling**
  - Failed records are published to **Amazon MQ** for later reprocessing

- **Dead Letter Strategy**
  - Ensures no data loss during failures

- **Comprehensive Logging**
  - Detailed logs for traceability and debugging

---

## 🔔 Notifications

- 📧 Email notifications are triggered for:
  - Successful execution
  - Failure scenarios

- 📊 Context-aware alerts based on application state

---

## 🛠️ CI/CD & Deployment

- **Version Control**: GitHub
- **CI/CD Pipeline**: GitHub Actions
- **Deployment Platform**: MuleSoft Anypoint Platform (CloudHub 2.0)

### Pipeline Capabilities:
- Automated build and validation
- Deployment to CloudHub 2.0
- Environment-based configuration support

---

## ⏱️ Scheduling

- The application is configured to run **once daily**
- Ensures timely synchronization of inventory data

---

## 🧩 Best Practices Followed

- MuleSoft streaming best practices
- Efficient resource utilization
- Fault-tolerant integration patterns
- Scalable and maintainable architecture
- Clean logging and monitoring strategy

---

## 📌 Summary

This project demonstrates how to design and implement a **scalable, fault-tolerant, and resource-efficient MuleSoft integration** capable of handling large data volumes under strict performance constraints.

It showcases expertise in:
- Large file processing
- Streaming and batch architecture
- Integration resilience patterns
- CloudHub 2.0 deployment
- CI/CD automation

---
