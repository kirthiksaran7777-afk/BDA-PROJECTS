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
# MapReduce Framework using Cricket Players

## Project Title
MapReduce Framework for Cricket Player Role Analysis

## Objective
The objective of this project is to implement a simple MapReduce framework in Python to analyze cricket player data. The program reads player information from a text file and counts the number of players in each role using the MapReduce process.

## Description
The project demonstrates the working of the MapReduce model through the following phases:

- Mapper
- Splitter
- Partitioner
- Sorter
- Reducer

The input data contains Player ID, Player Name, and Player Role. The output displays the total number of players in each role.

## Files

- `player.txt` – Input file containing player details.
- `playermapper.py` – Reads the input file and generates key-value pairs.
- `playersplitter.py` – Splits the mapper output for processing.
- `playerpartitioner.py` – Groups similar keys together.
- `playersorter.py` – Sorts the grouped data.
- `playerreducer.py` – Counts the number of players in each role.
- `playermaster.py` – Main program that executes all stages.

## Input Format

```
PlayerID,PlayerName,Role
```

Example:

```
101,Virat Kohli,Batsman
102,Rohit Sharma,Batsman
103,Jasprit Bumrah,Bowler
104,Hardik Pandya,All-Rounder
```

## Output

```
MAP OUTPUT
[('Batsman',1), ('Batsman',1), ('Bowler',1), ('All-Rounder',1)]

PARTITION OUTPUT
{'Batsman':[1,1], 'Bowler':[1], 'All-Rounder':[1]}

SORT OUTPUT
{'All-Rounder':[1], 'Batsman':[1,1], 'Bowler':[1]}

REDUCE OUTPUT
All-Rounder : 1
Batsman : 2
Bowler : 1
```

## Requirements

- Python 3.x
- Visual Studio Code

## How to Run

1. Place all project files in the same folder.
2. Open the folder in Visual Studio Code.
3. Open the terminal.
4. Run the command:

```bash
python playermaster.py
```

## Applications

- Cricket team analysis
- Player role statistics
- Learning MapReduce concepts
- Big Data processing simulation

## Conclusion

This project demonstrates the basic working of the MapReduce framework by processing cricket player data. It shows how data is mapped, split, partitioned, sorted, and reduced to produce meaningful results.
