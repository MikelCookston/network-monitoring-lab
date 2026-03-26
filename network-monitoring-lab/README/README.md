# 🌐 Network Monitoring Lab (AWS + Prometheus + Grafana)

## 📌 Overview

This project is a cloud-based network monitoring system built on AWS EC2 using Prometheus, Grafana, and Blackbox Exporter. It continuously monitors external endpoints and sends real-time alerts to Discord when connectivity issues are detected.

## ⚙️ Technologies Used

* AWS EC2 (Ubuntu)
* Prometheus
* Grafana
* Blackbox Exporter (ICMP monitoring)
* Node Exporter
* Discord Webhooks

## 🧠 What This Project Does

* Monitors external endpoints (1.1.1.1 and 8.8.8.8)
* Uses ICMP probes to detect connectivity issues
* Visualizes metrics in Grafana dashboards
* Sends real-time outage alerts to Discord
* Runs 24/7 in a cloud environment

## 🏗️ Architecture

* AWS EC2 instance hosts:

  * Prometheus (metrics collection)
  * Blackbox Exporter (network probing)
  * Grafana (visualization + alerting)
* Prometheus scrapes metrics from exporters
* Grafana queries Prometheus and triggers alerts
* Alerts are sent to Discord via webhook

## 🚨 Alerting Logic

* Internet **degraded**: one endpoint fails
* Internet **outage**: both endpoints fail
* Alert condition:

  * `avg(probe_success) < 0.1` → outage

## 📊 Dashboard

Displays:

* Endpoint availability
* Probe success metrics
* System health

## 📁 Project Structure

```
network-monitoring-lab/
├── README.md
├── configs/
│   ├── prometheus.yml
│   └── blackbox.yml
├── screenshots/
├── diagrams/
└── setup-guide.md
```

## 🛠️ Setup Summary

1. Launch AWS EC2 instance (Ubuntu)
2. Install Prometheus, Grafana, Blackbox Exporter
3. Configure Prometheus targets and exporters
4. Create Grafana dashboard
5. Configure alert rules
6. Integrate Discord webhook

## 💡 Key Skills Demonstrated

* Linux system administration
* Cloud infrastructure (AWS EC2)
* Monitoring & observability
* Network troubleshooting
* Alerting systems
* YAML configuration
* Real-world incident detection

## 📸 Screenshots

(See /screenshots folder)

## 📈 Future Improvements

* Add HTTPS monitoring
* Use Elastic IP for persistent access
* Add multiple regions/endpoints
* Implement Terraform for automation
