---

# Flink Fraud Detection with DataStream API

This repository consists of a **fraud detection system** that alerts on suspicious credit card transactions. Using a simple set of rules, it demonstrates how **Apache Flink** can implement advanced business logic and react in **real-time**.

## ✅ Prerequisites

* Java 8 or 11 installed and configured in your system.
* Maven installed (for building the Java project).

---

## 🛠️ Step-by-Step Setup Instructions

### ✅ 1. Start Flink Cluster (Locally)

You need to run the Flink runtime **locally** before executing your job.

#### 🔹 Option A: Start Flink Locally (without Docker)

If you don’t use Docker, follow these steps:

```bash
# Download Flink binary
wget https://archive.apache.org/dist/flink/flink-1.13.6/flink-1.13.6-bin-scala_2.12.tgz

# Extract the downloaded archive
tar -xzf flink-1.13.6-bin-scala_2.12.tgz

# Navigate into the Flink directory
cd flink-1.13.6

# Start the Flink cluster
./bin/start-cluster.sh
```

Flink's Web UI will be available at: [http://localhost:8081](http://localhost:8081)

Make sure the following configurations are set (in `conf/flink-conf.yaml`) to access the UI:

```
rest.port: 8081
rest.address: 0.0.0.0
```

---

### ✅ 2. Set Up and Run the Fraud Detection Project

#### 🔹 Create a Maven Project

```bash
mvn archetype:generate \
    -DarchetypeGroupId=org.apache.flink \
    -DarchetypeArtifactId=flink-walkthrough-datastream-java \
    -DarchetypeVersion=1.11.2 \
    -DgroupId=frauddetection \
    -DartifactId=frauddetection \
    -Dversion=0.1 \
    -Dpackage=spendreport \
    -DinteractiveMode=false
```

#### 🔹 Import and Build the Project

* Import the Java detector files into the generated Maven project.
* Then build the project using:

```bash
mvn clean package
```

This will generate a `.jar` file in the `target` directory.

---

### ✅ 3. Run the Fraud Detection Job

Assuming you're in the `flink-1.13.6` directory and the `frauddetection-0.1.jar` is copied here:

```bash
./bin/flink run ./frauddetection-0.1.jar
```

---

### ✅ 4. Monitor the Job

* Access Flink Web UI at [http://localhost:8081](http://localhost:8081)
* Monitor the cluster and running jobs.

---

### ✅ 5. Stop the Flink Cluster

```bash
./bin/stop-cluster.sh
```

---
