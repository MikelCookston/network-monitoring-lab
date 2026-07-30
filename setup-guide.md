# Setup Guide

This guide documents how I deployed a cloud-based network monitoring system using AWS EC2, Prometheus, Grafana, Blackbox Exporter, and a Raspberry Pi 5 connected securely through Tailscale.

## 1. Launch AWS EC2 Instance
- Deployed an Ubuntu-based EC2 instance in AWS
- Configured security group rules for:
  - SSH (22)
  - Grafana (3000)
  - Prometheus (9090)

## 2. Install Prometheus
- Downloaded Prometheus release binaries
- Created `/etc/prometheus/prometheus.yml`
- Configured Prometheus to scrape metrics from:
  - Prometheus
  - Node Exporter (AWS EC2)
  - Node Exporter (Raspberry Pi)
  - Blackbox Exporter

## 3. Install Node Exporter
- Installed Node Exporter on the EC2 instance
- Used it to collect:
  - CPU usage
  - memory usage
  - system health metrics
 
## 4. Configure Raspberry Pi Monitoring
- Installed Node Exporter on a Raspberry Pi 5
- Connected the Raspberry Pi to the AWS instance using Tailscale
- Configured Prometheus to securely scrape metrics over the Tailscale network

## 5. Install Blackbox Exporter
- Installed Blackbox Exporter for ICMP probing
- Configured probes for:
  - 1.1.1.1
  - 8.8.8.8
- Used probe success metrics for outage detection

## 6. Configure Grafana
- Installed Grafana on the EC2 instance
- Added Prometheus as the data source
- Built dashboard panels for:
  - CPU usage (AWS & Raspberry Pi)
  - Memory usage (AWS & Raspberry Pi)
  - Internet latency
  - Internet reachability

## 7. Configure Alerts
- Created Grafana alert rules for:
  - Home network connectivity
  - Internet reachability
- Configured Discord webhook notifications
- Verified outage and recovery notifications

## 8. Validate Monitoring
- Verified all Prometheus scrape targets were UP
- Confirmed Grafana displayed live metrics
- Tested Discord outage notifications
- Tested Discord recovery notifications
- Verified Raspberry Pi metrics were collected through Tailscale

## Result
The completed monitoring system securely collects metrics from an AWS EC2 instance and a Raspberry Pi 5 over Tailscale, visualizes system health in Grafana, and sends real-time Discord notifications whenever connectivity issues are detected or resolved.
