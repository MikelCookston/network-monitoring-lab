# Setup Guide

This guide documents how I deployed a cloud-based network monitoring system on AWS EC2 using Prometheus, Grafana, Node Exporter, and Blackbox Exporter.

## 1. Launch AWS EC2 Instance
- Deployed an Ubuntu-based EC2 instance in AWS
- Configured security group rules for:
  - SSH (22)
  - Grafana (3000)
  - Prometheus (9090)

## 2. Install Prometheus
- Downloaded Prometheus release binaries
- Created `/etc/prometheus/prometheus.yml`
- Configured Prometheus to scrape:
  - itself
  - Node Exporter
  - Blackbox Exporter

## 3. Install Node Exporter
- Installed Node Exporter on the EC2 instance
- Used it to collect:
  - CPU usage
  - memory usage
  - system health metrics

## 4. Install Blackbox Exporter
- Installed Blackbox Exporter for ICMP probing
- Configured probes for:
  - 1.1.1.1
  - 8.8.8.8
- Used probe success metrics for outage detection

## 5. Configure Grafana
- Installed Grafana on the EC2 instance
- Added Prometheus as the data source
- Built dashboard panels for:
  - latency / probe duration
  - internet reachability
  - CPU usage
  - memory usage

## 6. Configure Alerts
- Created alert rules in Grafana
- Alert condition used:
  - average probe success across external endpoints
- Configured Discord webhook notifications for outage alerts

## 7. Validate Monitoring
- Verified Prometheus targets were UP
- Confirmed Grafana dashboard displayed live metrics
- Tested alerting workflow with Discord notifications

## Result
The final system provides cloud-hosted, always-on network monitoring and real-time outage alerting.
