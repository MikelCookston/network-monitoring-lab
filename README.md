# 🌐 Network Monitoring Lab (AWS + Prometheus + Grafana)

## 📌 Overview
This project is a cloud-based network monitoring system built using AWS EC2, Prometheus, Grafana, Blackbox Exporter, and a Raspberry Pi 5 connected securely through Tailscale. It monitors both internet connectivity and the health of a remote home device, sending real-time Discord notifications whenever connectivity issues are detected or resolved.

## ⚙️ Technologies Used
* AWS EC2 (Ubuntu)
* Raspberry Pi 5
* Tailscale
* Prometheus
* Grafana
* Blackbox Exporter
* Node Exporter
* Discord Webhooks

## 🧠 What This Project Does
* Monitors internet connectivity using ICMP probes (1.1.1.1 and 8.8.8.8)
* Collects CPU and memory metrics from both AWS EC2 and a Raspberry Pi
* Securely scrapes Raspberry Pi metrics over Tailscale
* Visualizes metrics in Grafana dashboards
* Sends Discord notifications when connectivity is lost or restored
* Runs 24/7 in the cloud

## 🏗️ Architecture

```
                   Internet
                        │
              1.1.1.1 / 8.8.8.8
                        │
                AWS EC2 (Ubuntu)
        ┌─────────────────────────┐
        │ Prometheus              │
        │ Grafana                 │──────────────► Discord
        │ Blackbox Exporter       │
        └───────────┬─────────────┘
                    │
               Tailscale VPN
                    │
        ┌───────────▼─────────────┐
        │ Raspberry Pi 5          │
        │ Node Exporter           │
        └─────────────────────────┘
```
## 🚨 Alerting Logic
The system includes two alert types:

* **Home Network Connectivity**
  * Detects when the Raspberry Pi becomes unreachable.
  * Sends outage and recovery notifications through Discord.

* **Internet Reachability**
  * Monitors external connectivity using ICMP probes.
  * Detects degraded or unavailable external network connectivity.


## 📊 Dashboard
Displays:

* CPU usage (AWS & Raspberry Pi)
* Memory usage (AWS & Raspberry Pi)
* Internet latency
* Internet reachability
* Discord alert notifications

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
3. Install Node Exporter on AWS and Raspberry Pi
4. Connect Raspberry Pi using Tailscale
5. Configure Prometheus targets
6. Create Grafana dashboards
7. Configure Discord alerts

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
* Dockerize Prometheus and Grafana
* Implement Terraform
* Monitor additional home devices
* Add multiple monitoring regions/endpoints
