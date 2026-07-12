<div align="center">

# 🚀 SFA Monitoring Dashboard

### Enterprise Store Device Monitoring & Footfall Analytics Platform

Built with **Grafana**, **Prometheus**, **Blackbox Exporter**, **Alertmanager**, and **MySQL**

Monitor device health, connectivity, uptime, latency, outages, and footfall analytics across all retail stores from a single dashboard.

---

![Grafana](https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white)
![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Alertmanager](https://img.shields.io/badge/Alertmanager-FF6B00?style=for-the-badge)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)

</div>

---

# 📖 Overview

The **SFA Monitoring Dashboard** is a centralized monitoring platform designed to provide real-time visibility into the health and availability of Store Footfall Analytics (SFA) devices deployed across multiple retail locations.

The solution combines infrastructure monitoring with business analytics, enabling support teams to proactively detect outages, monitor device performance, validate footfall collection, and ensure operational continuity.

---

# 🎯 Key Objectives

✅ Monitor SFA device availability

✅ Detect complete store outages

✅ Measure fleet uptime

✅ Track device latency

✅ Identify unstable ("flapping") devices

✅ Monitor footfall collection

✅ Detect unregistered devices

✅ Generate proactive alerts

✅ Centralize operational visibility

---

# 🏗️ Solution Architecture

```text
                        +----------------+
                        |    Grafana     |
                        | Visualization  |
                        +--------+-------+
                                 |
                    +------------+------------+
                    |                         |
                    v                         v

           +----------------+       +----------------+
           |  Prometheus    |       |     MySQL      |
           | Metrics Store  |       | Footfall Data  |
           +--------+-------+       +--------+-------+
                    |                         |
                    |                         |
                    v                         |
          +-------------------+              |
          | Blackbox Exporter |              |
          | ICMP Monitoring   |              |
          +---------+---------+              |
                    |                        |
                    |                        |
                    v                        |
          +-------------------+             |
          |   SFA Devices     |-------------+
          | Retail Stores     |
          +-------------------+
```

---

# 📊 Dashboard Features

## Device Health Dashboard

Provides a high-level operational overview of the entire SFA fleet.

### Metrics

- Fleet Uptime %
- Online Devices
- Offline Devices
- Connectivity Ratio
- Device Availability
- Device Inventory
- Store Connectivity Status

### Visualizations

- Fleet Health Summary
- Online vs Offline Trend
- Device Availability Tables
- Connectivity Ratio Chart
- Offline Devices List

---

## Device Inventory Dashboard

Tracks every monitored SFA device.

### Information Displayed

- Store Name
- Device Name
- IP Address
- MAC Address
- Device Status
- Connectivity State

### Benefits

- Device inventory validation
- Asset visibility
- Rapid troubleshooting
- Deployment verification

---

## Connectivity Dashboard

Tracks network performance and device behavior.

### Metrics

- Ping Success Rate
- Response Time
- Device Uptime %
- Connectivity History

### Visualizations

- Ping Latency Trend
- Uptime Ranking
- Device Status History

---

## Flapping Device Detection

Identifies unstable devices experiencing frequent transitions.

### Monitoring

- Up → Down Events
- Down → Up Events
- Transition Frequency

### Benefits

- Early failure detection
- Network instability analysis
- SLA improvement

---

## Inventory Validation Dashboard

Detects discrepancies between the database and monitoring platform.

### Shows

- Devices present in database
- Devices monitored by Prometheus
- Missing devices
- Unregistered devices

### Benefits

- Inventory reconciliation
- Deployment audit
- Monitoring coverage validation

---

# 👥 Footfall Analytics Dashboard

Tracks store traffic collected by SFA devices.

### Metrics

- Live Footfall
- Last Completed Hour
- Daily Counts
- Store Comparison
- Historical Data Trends

### Store Performance Visibility

Allows operations teams to verify:

- Data collection health
- Store traffic trends
- Missing footfall records
- Sensor outages

---

# 🚨 Alerting

Alertmanager provides proactive notifications.

## Device Down Alert

Triggered when:

```promql
probe_success == 0
```

Duration:

```yaml
for: 10m
```

---

## Store Down Alert

Triggered when all SFA devices in a store become unreachable.

Example:

```promql
count by (store) (probe_success == 1) == 0
```

Severity:

```yaml
critical
```

---

## Flapping Device Alert

Generated when devices exceed normal transition thresholds over a defined period.

---

# ⚙️ Technology Stack

| Component | Purpose |
|------------|----------|
| Grafana | Dashboards & Visualizations |
| Prometheus | Metrics Collection |
| Blackbox Exporter | ICMP Monitoring |
| Alertmanager | Notifications |
| MySQL | Footfall Data Source |
| Docker | Container Runtime |
| Docker Compose | Service Orchestration |

---

# 📂 Repository Structure

```text
SFA-Monitoring-Dashboard
│
├── docker-compose.yml
│
├── grafana/
│   ├── dashboards/
│   ├── datasources/
│   └── provisioning/
│
├── prometheus/
│   ├── prometheus.yml
│   ├── rules/
│   └── targets/
│
├── blackbox/
│   └── blackbox.yml
│
├── alertmanager/
│   └── alertmanager.yml
│
└── README.md
```

---

# 🚀 Deployment

## Clone Repository

```bash
git clone https://github.com/ashrafelgohary/SFA-Monitoring-Dashboard.git
```

```bash
cd SFA-Monitoring-Dashboard
```

---

## Start Services

```bash
docker compose up -d
```

---

## Verify Running Containers

```bash
docker ps
```

---

# 📈 Monitored KPIs

## Connectivity KPIs

- Device Availability %
- Fleet Uptime %
- Online Devices
- Offline Devices
- Outage Duration

## Network KPIs

- ICMP Response Time
- Packet Loss
- Availability Trend

## Business KPIs

- Live Footfall
- Hourly Footfall
- Daily Footfall
- Store Comparison

---

# 🔐 Security

The platform is designed to run entirely within the internal corporate infrastructure.

Recommended practices:

- Restrict Grafana access
- Change default credentials
- Use HTTPS
- Protect Prometheus endpoints
- Secure Alertmanager webhooks

---

# 📋 Use Cases

- Retail Store Monitoring
- Device Availability Monitoring
- Infrastructure Operations
- Store Connectivity Management
- Footfall Analytics Validation
- NOC Visibility
- Incident Management
- SLA Tracking

---

# 🔮 Future Enhancements

- SMS Notifications
- WhatsApp Integration
- Teams Integration
- Predictive Analytics
- Device Auto-Discovery
- SLA Reporting
- Capacity Planning
- AI-Based Anomaly Detection

---

# 👨‍💻 Author

### Ashraf Hassan

**Systems Support Engineer**

Infrastructure Automation | Monitoring | DevOps | Enterprise Operations

GitHub:
https://github.com/ashrafelgohary

---

# ⭐ Support

If this project helps your monitoring operations, consider giving it a ⭐ on GitHub.

---

<div align="center">

Built with ❤️ using Grafana, Prometheus and Automation

</div>
