🚀 Day 5 – Multi-Channel Notification System with Error Handling & Retry Engine (n8n)
📌 Overview

This project demonstrates a production-style automation system built using n8n that processes incoming leads, sends multi-channel notifications, logs failures, and enables retry of failed operations.

The system simulates real-world SaaS architecture patterns including event-driven workflows, error observability, and recovery mechanisms.

🏗️ System Architecture
Workflow 1 — Lead Processing Pipeline
Receives lead via webhook (Tally form)
Extracts structured data
Sends Slack notification
Sends Gmail confirmation
Workflow 2 — Error Monitoring System
Triggered automatically when Workflow 1 fails
Filters errors using workflow name
Logs structured error data into Google Sheets
Workflow 3 — Retry & Recovery System
Manually triggered
Reads failed records from Google Sheets
Rebuilds usable lead data
Resends Slack + Gmail notifications
🔁 End-to-End Flow
Tally Form
   ↓
Webhook (Workflow 1)
   ↓
Slack + Gmail
   ↓
(If failure occurs)
   ↓
Error Trigger (Workflow 2)
   ↓
Google Sheets (Error Log)
   ↓
Manual Retry (Workflow 3)
   ↓
Recovered Slack + Gmail delivery
⚙️ Key Features
Multi-channel notification system (Slack + Email)
Centralized error logging system
Workflow-level error tracking
Manual retry mechanism
Data reconstruction from stored payloads
Separation of concerns across workflows
🧠 Key Learnings
Event-driven architecture in automation systems
Importance of observability in production workflows
Difference between logs and actual application state
Designing retryable workflows using persistent storage
Failure handling strategies in distributed systems
⚠️ Limitations
Google Sheets used as a lightweight queue (not production-grade)
Manual retry process (no auto-retry logic)
Partial payload storage in early implementation
🚀 Future Improvements
Implement queue system (Redis / RabbitMQ)
Add automatic retry with exponential backoff
Store full event payload for true replay capability
Add success/failure tracking dashboard
Implement dead-letter queue (DLQ)
👩🏽‍💻 Tech Stack
n8n automation platform
Google Sheets (error storage)
Slack API
Gmail API
Webhooks (Tally Forms