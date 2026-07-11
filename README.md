# BigBasket Distributed Log Collection System

## Project Overview

The **BigBasket Distributed Log Collection System** is a Python-based distributed logging application that simulates multiple BigBasket warehouse servers generating real-time logs. A multithreaded log harvester collects these logs over TCP sockets, validates them, partitions them based on warehouse and log severity, stores them in compact binary format, and later reconstructs them into human-readable logs.

This project demonstrates concepts of:

* Socket Programming
* Multithreading
* Regular Expressions
* Binary File Handling
* Dynamic Partitioning
* Data Serialization

---

# Domain

**BigBasket Online Grocery Delivery Platform**

The system simulates log generation from multiple BigBasket warehouse locations.

* BigBasket Chennai
* BigBasket Bangalore
* BigBasket Mumbai

---

# Objectives

* Simulate multiple warehouse log servers.
* Collect logs using TCP socket communication.
* Validate incoming log records using Regular Expressions.
* Partition logs dynamically according to warehouse and log severity.
* Store logs in compact binary format.
* Recover binary logs into readable format.

---

# Technologies Used

* Python 3.x
* Socket Programming
* Multithreading
* Regular Expressions (Regex)
* Binary File Handling
* Struct Module
* File System Operations

---

# Project Structure

```
BigBasket_Log_System/

│
├── log_server.py
├── log_harvester.py
├── read_binary.py
├── partitions/
│      ├── bigbasket-chennai_INFO.bin
│      ├── bigbasket-chennai_ERROR.bin
│      ├── bigbasket-bangalore_WARNING.bin
│      ├── ...
│
└── README.md
```

---

# Modules Description

## 1. log_server.py

Simulates three BigBasket warehouse servers.

Responsibilities

* Starts three TCP servers.
* Generates random warehouse log messages.
* Sends continuous log streams.
* Sends occasional corrupted log entries for testing.

Warehouse Servers

* bigbasket-chennai
* bigbasket-bangalore
* bigbasket-mumbai

---

## 2. log_harvester.py

Main processing component.

Responsibilities

* Connects to all warehouse servers.
* Reads incoming TCP streams.
* Performs manual socket slicing.
* Validates logs using Regex.
* Converts logs into structured dictionaries.
* Dynamically creates partition files.
* Stores logs in binary format.
* Displays live ingestion statistics.

---

## 3. read_binary.py

Responsibilities

* Reads binary partition files.
* Decodes binary records.
* Displays human-readable log entries.

---

# Log Format

```
YYYY-MM-DD HH:MM:SS | LEVEL | SERVICE | MESSAGE
```

Example

```
2026-07-10 15:10:12 | INFO | bigbasket-chennai | Order#4321 packed at warehouse
```

---

# Binary Record Structure

Each record is stored in binary format.

| Field          | Size     |
| -------------- | -------- |
| Timestamp      | 19 Bytes |
| Log Level      | 1 Byte   |
| Service Length | 2 Bytes  |
| Service Name   | Variable |
| Message Length | 2 Bytes  |
| Message        | Variable |

Each record is also prefixed with a **4-byte length field**.

---

# Log Levels

* DEBUG
* INFO
* WARNING
* ERROR

---

# Dynamic Partitioning

Logs are automatically partitioned based on:

```
Warehouse + Log Level
```

Examples

```
bigbasket-chennai_INFO.bin

bigbasket-chennai_ERROR.bin

bigbasket-bangalore_WARNING.bin

bigbasket-mumbai_DEBUG.bin
```

---

# Features

* Multi-threaded socket communication
* Real-time log collection
* Regex-based validation
* Automatic rejection of corrupted logs
* Dynamic binary partition creation
* Binary serialization
* Binary deserialization
* Live statistics dashboard


# Expected Output

* Warehouse servers continuously generate logs.
* Harvester collects logs from all servers.
* Logs are validated successfully.
* Corrupted logs are rejected.
* Binary partition files are created dynamically.
* Binary logs are successfully decoded into readable format.

---

# Learning Outcomes

After completing this project, you will understand:

* Distributed log collection
* TCP socket communication
* Multithreading in Python
* Binary file storage
* Data serialization and deserialization
* Dynamic partitioning techniques
* Regular expression validation
* Real-time data processing

---

# Future Enhancements

* Database integration (MySQL or MongoDB)
* Kafka-based log streaming
* Hadoop Distributed File System (HDFS) storage
* Spark Streaming for real-time analytics
* Log compression
* Web dashboard for monitoring
* Cloud deployment on AWS or Azure

---

# Conclusion

The **BigBasket Distributed Log Collection System** demonstrates a complete pipeline for real-time log generation, collection, validation, partitioning, binary storage, and retrieval. It highlights key distributed systems concepts such as multithreading, socket communication, binary serialization, and dynamic partition management, making it a practical mini-project for Big Data and Distributed Systems coursework.
