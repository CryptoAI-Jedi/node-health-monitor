# Node Health Monitor 

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Docker](https://img.shields.io/badge/docker-v24.0+-blue.svg)
![Prometheus](https://img.shields.io/badge/prometheus-v2.45+-orange.svg)
![Grafana](https://img.shields.io/badge/grafana-v10.0+-orange.svg)

**A production-grade monitoring stack for Blockchain Nodes (Bitcoin, Monero) and Infrastructure.**

This project provides a containerized observability solution for tracking the health, uptime, and performance of crypto nodes running on the same underlying bare-metal hardware. It leverages **Prometheus** for metric scraping and **Grafana** for visualization, orchestrated via **Docker Compose**.

---

## Dashboard Preview

![Dashboard Screenshot](./screenshots/dashboard-screenshot.png)

---

## Features

- **Multi-Chain Support**: Pre-configured scraping for Bitcoin Core and Monero nodes.
- **Infrastructure Monitoring**: Real-time tracking of CPU, RAM, Disk I/O, and Network traffic via Node Exporter.
- **Containerized Architecture**: One-command deployment using Docker Compose.
- **Optimized Configuration**:
  > *This configuration uses a 15s global scrape interval to balance resolution with storage costs. It separates 'System Metrics' (CPU/RAM) from 'Chain Metrics' (Block Height) to optimize load, as blockchain states change slower than system resources.*

## Tech Stack

- **Prometheus**: Time-series database for metric collection.
- **Grafana**: Visualization and alerting dashboard.
- **Node Exporter**: Hardware and OS metrics.
- **Bitcoin-Prometheus-Exporter**: RPC-based metrics for Bitcoin Core.
- **Monero-Exporter**: Metrics for Monero Daemon (monerod).
- **Docker & Docker Compose**: Container orchestration.

## Installation & Usage

### Prerequisites
- Docker & Docker Compose installed.
- Running instances of `bitcoind` and `monerod` (optional, exporters will retry connection).

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/CryptoAI-Jedi/node-health-monitor.git
   cd node-health-monitor

2. **Start the Stack**
   ```bash
   docker-compose up -d

3. **Access the Dashboards**
- Grafana: http://localhost:3000 (Default login: admin / admin)
- Prometheus: http://localhost:9090

**Configuration Details**
- prometheus.yml: Defines scrape jobs and intervals.
- docker-compose.yml: Orchestrates the service mesh and networking.

**Future Roadmap**
- Add Alertmanager for Telegram/Slack/Discord notifications on peer drop.
- Integrate ASIC mining fleet stats via custom Python gateway.
- Create a unified "Ops Center" dashboard panel.

---

Maintained by [CryptoAI-Jedi](https://github.com/CryptoAI-Jedi)
