# Doyouok — Lightweight Cron Job & Workflow Monitoring

[![Website](https://img.shields.io/badge/Website-doyouok.com-blue?style=flat-square)](https://doyouok.com)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

**Doyouok** is a lightweight, zero-install monitoring service for **cron jobs, background tasks, database backups, and automation workflows**.

It helps you detect jobs that **silently fail, stop running, or never complete**, and alerts you when a scheduled job misses its expected check-in.

> **If your job doesn't say "I'm OK", Doyouok lets you know.**

---

## 🚀 How It Works

Doyouok uses a simple **HTTP heartbeat / ping** mechanism.

```text
Your Job / Script
       │
       │  HTTP Ping
       ▼
┌─────────────────┐
│     Doyouok     │
│  Monitor Check  │
└────────┬────────┘
         │
         │ No check-in
         ▼
   🔔 Alert You
```

### 1. Create a Check

Create a monitor on [**Doyouok**](https://doyouok.com) and get a unique HTTP Ping URL.

### 2. Ping When Your Job Succeeds

Add a simple HTTP request to the end of your script or workflow.

### 3. Get Alerted When It Stops

If Doyouok doesn't receive a check-in within the expected interval, you'll receive an alert.

---

## 🛠 Quickstart

### Cron / Shell Script

Add a `curl` request after your job completes successfully:

```bash
0 * * * * /path/to/backup.sh && curl -fsS https://ping.doyouok.com/ping/YOUR-API-KEY
```

The `&&` ensures Doyouok is notified **only when the job succeeds**.

---

### Python

```python
import requests

# Perform your automation / backup task
print("Executing job...")

# Notify Doyouok after successful completion
response = requests.get(
    "https://ping.doyouok.com/ping/YOUR-API-KEY",
    timeout=10
)

response.raise_for_status()

print("Doyouok check-in successful.")
```

---

### n8n / Zapier / Make

Doyouok works with automation platforms that can make HTTP requests.

Simply add an **HTTP Request** step at the end of your workflow and call your Doyouok Ping URL:

```text
https://ping.doyouok.com/ping/YOUR-API-KEY
```

This makes it easy to monitor workflows that otherwise have no built-in failure notification.

---

## 💡 What Can You Monitor?

Doyouok is useful for monitoring:

* ⏰ Cron jobs
* 💾 Database backups
* 📦 Data import/export jobs
* 🔄 Background workers
* 🐍 Python scripts
* 🐚 Shell scripts
* ⚙️ Scheduled automation
* 🔗 n8n workflows
* 🤖 Zapier / Make automations
* 🖥️ Server maintenance tasks
* 📊 ETL and data pipelines

If something runs on a schedule and you need to know when it stops running, **Doyouok can monitor it**.

---

## ✨ Why Doyouok
