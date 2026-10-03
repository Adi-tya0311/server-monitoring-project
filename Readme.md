# Linux Server Monitoring & Alerting with Prometheus and Grafana

A hands-on DevOps project for monitoring two Linux servers on AWS EC2 using **Prometheus, Node Exporter, and Grafana**, with email notifications for CPU usage alerts.

The project was built to understand how infrastructure metrics are collected, visualized, and turned into actionable alerts.

---

## 📌 Project Overview

This project monitors two Linux servers running on **AWS EC2**.

**Node Exporter** runs on both servers and exposes system-level metrics such as CPU, memory, disk, and network statistics.

**Prometheus** collects these metrics and stores them for monitoring and querying.

**Grafana** connects to Prometheus and provides dashboards for visualizing the server metrics.

A **Grafana CPU alert** was also configured to send an email notification when CPU usage remains above the configured threshold.

---

## 🏗️ Architecture

```text
                    AWS EC2
              ┌───────────────────┐
              │                   │
              │    Server 1       │
              │  Monitoring       │
              │                   │
              │  Node Exporter    │
              │  Prometheus       │
              │  Grafana          │
              │                   │
              └─────────┬─────────┘
                        │
                        │ Metrics
                        │
              ┌─────────▼─────────┐
              │                   │
              │    Server 2       │
              │   Target Server   │
              │                   │
              │  Node Exporter    │
              │                   │
              └───────────────────┘


Node Exporter
      │
      ▼
 Prometheus
      │
      ▼
   Grafana
      │
      ▼
 Gmail Alert