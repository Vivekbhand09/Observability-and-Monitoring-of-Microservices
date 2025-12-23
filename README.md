# 🔍 Observability and Monitoring in EazyBank Microservices

This section represents an **advanced evolution** of the EazyBank microservices architecture, where the focus shifts from **resiliency** to **deep visibility, performance insights, and proactive system health management**.

By adding **observability and monitoring**, the system becomes easier to **debug, analyze, and operate in production**.

---

## 🚧 Challenges We Are Solving

### 1️⃣ Hard to Identify Failures

**Problem:**
When something breaks in a microservices system, it becomes difficult to know:
- ❓ Which service failed
- ❓ Where exactly the bug occurred
- ❓ How the request traveled across multiple services

**Solution (Observability):**
Collect and combine:
- 📄 Logs from all services
- 🧩 Centralize logs in one place
- 🔎 Make logs searchable

This allows developers to **quickly trace issues and identify root causes**.

---

### 2️⃣ Monitoring Performance of Service Calls

**Problem:**
You need visibility into:
- ⏱️ How long each service takes to respond
- 🐌 Where the request became slow
- 🚫 Which service is the bottleneck

**Solution (Observability + Tracing):**
- Track the **entire request journey** across services
- Measure:
  - Latency
  - Response time
  - Failures

This is achieved using **distributed tracing tools**.

---

### 3️⃣ Monitoring Service Metrics & Health

**Problem:**
In production, you must constantly monitor:
- 🧠 CPU usage
- 🧵 JVM memory usage
- 💽 Disk usage
- ❌ Error rates
- ❤️ Health of every microservice

**Solution (Monitoring):**
Use monitoring tools to:
- 📊 Show real-time dashboards
- 🚨 Trigger alerts when thresholds are crossed
- 📢 Notify teams **before outages occur**

---

> **Observability + Monitoring together help identify and resolve issues in microservices *before* they impact users or cause outages.**

---

## 👀 What Is Observability?

### 📘 Definition

**Observability** is the ability to **understand the internal state of a system by analyzing the data it produces**, such as logs, metrics, and traces, without modifying the system itself.

In microservices, observability answers:
- *Why* did this failure happen?
- *Where* did the latency occur?
- *How* did a request flow through services?

Observability focuses on **unknown and unexpected problems**.

---

## 🧱 Three Pillars of Observability

### 1️⃣ Metrics 📊

**What they are:**
- Numerical measurements collected over time

**Examples:**
- Request count
- Response time
- Error rate
- CPU & memory usage

**Why they matter:**
- Help detect trends
- Enable alerting
- Provide high-level system health

---

### 2️⃣ Logs 📄

**What they are:**
- Timestamped, structured or unstructured event records

**Examples:**
- Error messages
- Debug information
- Business events

**Why they matter:**
- Help debug issues
- Provide detailed context
- Useful for root cause analysis

---

### 3️⃣ Traces 🧭

**What they are:**
- End-to-end view of a request as it flows through multiple services

**Includes:**
- Service-to-service hops
- Time spent in each service
- Failures and delays

**Why they matter:**
- Identify performance bottlenecks
- Understand request flow
- Debug distributed systems

---

## 📡 What Is Monitoring?

### 📘 Definition

**Monitoring** is the practice of **collecting, visualizing, and alerting on predefined system metrics and health indicators** to ensure systems are operating within expected limits.

Monitoring focuses on **known problems** and system stability.

---

### 🎯 Why Monitoring Is Important in Microservices

- 🔄 Detect service downtime early
- 📈 Track resource usage trends
- 🚨 Alert teams before failures escalate
- 📊 Ensure SLAs and performance goals
- 🧠 Maintain operational confidence

---

## 🔍 Observability vs Monitoring

| Aspect | Observability | Monitoring |
|------|--------------|------------|
| Purpose | Understand *why* something happened | Detect *when* something is wrong |
| Focus | Unknown & complex issues | Known issues |
| Data | Logs, Metrics, Traces | Mostly Metrics |
| Scope | Deep system behavior | System health |
| Debugging | Root cause analysis | Alert-based investigation |
| Reactive / Proactive | Proactive insights | Mostly reactive |
| Usage | Developers & SREs | Ops & Support teams |

---
## 📝 Logging in EazyBank Microservices

Logging is a **core foundation** of observability. Before metrics and traces, logs are usually the **first signal** that something is wrong in a system.

---

## 📘 What Is Logging?

### 🔍 Detailed Definition

**Logging** is the process of **recording events, messages, and contextual information** produced by an application while it is running.

In microservices, logging helps answer questions like:
- What happened?
- When did it happen?
- In which service did it happen?
- What was the request or error context?

Logs act as a **historical record of system behavior**, making them essential for:
- Debugging issues
- Root cause analysis
- Auditing and compliance
- Understanding runtime behavior

In distributed systems like microservices, logs must be:
- **Centralized**
- **Searchable**
- **Correlated across services**

Without centralized logging, debugging becomes extremely difficult.

---

## 📊 Log Levels Explained

Log levels define the **severity and importance** of log messages.

### 1️⃣ TRACE 🧵
- Most detailed level
- Used for **very fine-grained debugging**
- Shows method-level or step-by-step execution
- Typically disabled in production

---

### 2️⃣ DEBUG 🐞
- Used for debugging during development
- Shows internal application state
- Helps developers understand logic flow

---

### 3️⃣ INFO ℹ️
- General application events
- Indicates normal system behavior
- Commonly enabled in production

---

### 4️⃣ WARN ⚠️
- Indicates potential problems
- System continues to work but something looks abnormal

---

### 5️⃣ ERROR ❌
- Serious issues that caused a failure
- Requires immediate attention

---

## 🧠 Why Centralized Logging Is Needed

In a microservices architecture:
- Each service runs independently
- Each service generates its own logs
- Logs are spread across multiple containers/VMs

👉 **Centralized logging** solves this by:
- Collecting logs from all services
- Storing them in one place
- Making them searchable and filterable

---

## 📦 Managing Logs with Grafana Stack

EazyBank uses the **Grafana Observability Stack** for logging:
- **Grafana** → Visualization & querying
- **Loki** → Log storage & indexing
- **Alloy** → Log collection & forwarding

---

## 📊 Grafana (Visualization Layer)

### 📘 What Is Grafana?

**Grafana** is an **open-source observability and visualization platform** used to explore, query, and visualize logs, metrics, and traces.

Grafana provides:
- Interactive dashboards
- Powerful query capabilities
- Unified view of observability data

### 🎯 Role of Grafana in Logging

- Connects to Loki as a data source
- Displays logs in real time
- Allows filtering by:
  - Service name
  - Log level
  - Time range
- Helps developers quickly identify issues

Grafana acts as the **single pane of glass** for observability.

---

## 🗄️ Loki (Log Storage Layer)

### 📘 What Is Loki?

**Grafana Loki** is a **log aggregation and storage system** designed specifically for cloud-native and microservices environments.

Unlike traditional log systems:
- Loki does **not index full log content**
- It indexes only **metadata (labels)**

### 🧠 Why Loki Is Efficient

- Lower storage cost
- Faster ingestion
- Scales easily with microservices

### 🎯 Role of Loki

- Receives logs from Alloy
- Stores logs efficiently
- Indexes logs using labels like:
  - service name
  - environment
  - log level

Loki is optimized for **high-volume, low-cost log storage**.

---

## 🚚 Alloy (Log Collector)

### 📘 What Is Alloy?

**Grafana Alloy** is a **unified telemetry collector** used to collect and forward:
- Logs
- Metrics
- Traces

(Alloy is the modern evolution of Promtail.)

### 🎯 Role of Alloy in Logging

- Runs alongside microservices
- Reads logs from:
  - Application files
  - Containers
  - Standard output
- Adds labels (service name, instance, env)
- Sends logs to Loki

Alloy acts as the **bridge between microservices and Loki**.

---

## 🔄 Logging Flow in EazyBank

### 🧩 End-to-End Log Flow

1️⃣ **Microservices generate logs**  
Each service (Accounts, Loans, Cards, Gateway) writes logs during execution.

2️⃣ **Alloy collects the logs**  
Alloy reads logs, enriches them with metadata, and prepares them for storage.

3️⃣ **Loki stores the logs**  
Loki receives logs from Alloy and stores them efficiently using labels.

4️⃣ **Grafana displays the logs**  
Grafana queries Loki and displays logs in a searchable, visual format.

---

## 🔁 Logging Architecture Flow

```text
Microservices
      ↓
   Grafana Alloy
      ↓
      Loki
      ↓
   Grafana UI

```
---
