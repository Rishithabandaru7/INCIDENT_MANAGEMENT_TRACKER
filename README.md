<h1 align="center">📊 Incident Management Tracker</h1>

<p align="center">
  A <b>full-stack DevOps project</b> with a complete CI/CD pipeline, containerized deployment, and real-time monitoring dashboards — built to simulate production-grade SRE workflows.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=kubernetes&logoColor=white"/>
  <img src="https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white"/>
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>
  <img src="https://img.shields.io/badge/Prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white"/>
  <img src="https://img.shields.io/badge/Grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white"/>
</p>

---

## ✨ Features

- 🚀 **Full CI/CD Pipeline** — Automated build, test, and deploy via Jenkins
- 🐳 **Containerized App** — Dockerized Flask app with Nginx reverse proxy
- ☸️ **Kubernetes Deployment** — Zero-downtime rolling deployments with K8s manifests
- 📈 **Real-Time Monitoring** — Prometheus metrics + Grafana dashboards for 100% uptime visibility
- 🚨 **Alerting** — Prometheus alert rules for incident detection (CPU, memory, request errors)
- 🗄️ **Database** — MySQL for persistent incident storage

---

## 🏗️ Architecture

```
Developer Push (Git)
        │
        ▼
   Jenkins CI/CD
        │
   ┌────┴────┐
   │  Build  │  Docker image build
   │  Test   │  Run test suite
   │  Push   │  Push to Docker Hub
   └────┬────┘
        │
        ▼
  Kubernetes Cluster
  ┌─────────────────────────┐
  │  Nginx (reverse proxy)  │
  │        │                │
  │   Flask App (pods)      │
  │        │                │
  │   PostgreSQL (DB)       │
  └─────────────────────────┘
        │
        ▼
  Prometheus (scrapes metrics)
        │
        ▼
  Grafana (dashboards + alerts)
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Backend | Python (Flask) |
| Frontend | HTML, CSS, JavaScript |
| Database | MySQL |
| Containerization | Docker, Docker Compose |
| Orchestration | Kubernetes (K8s) |
| CI/CD | Jenkins |
| Reverse Proxy | Nginx |
| Monitoring | Prometheus |
| Dashboards | Grafana |

---

## 📁 Project Structure

```
INCIDENT_MANAGEMENT_TRACKER/
├── app.py                # Flask backend — REST API
├── db.py                 # PostgreSQL database operations
├── Dockerfile            # Docker image definition
├── docker-compose.yml    # Multi-container local setup
├── init.sql              # Database schema initialization
├── requirements.txt      # Python dependencies
├── k8s/                  # Kubernetes manifests
│   ├── deployment.yaml
│   ├── service.yaml
│   └── configmap.yaml
├── nginx/                # Nginx reverse proxy config
├── static/               # CSS and JS assets
└── templates/            # HTML templates (Jinja2)
```

---

## 🚀 Getting Started

### Prerequisites
- Docker & Docker Compose
- Kubernetes cluster (Minikube or cloud)
- Jenkins (for CI/CD)

### Run Locally with Docker Compose

```bash
# Clone the repo
git clone https://github.com/Rishithabandaru7/INCIDENT_MANAGEMENT_TRACKER.git
cd INCIDENT_MANAGEMENT_TRACKER

# Start all services
docker-compose up --build
```

App runs at `http://localhost:80`

### Deploy to Kubernetes

```bash
# Apply all K8s manifests
kubectl apply -f k8s/

# Check deployment status
kubectl get pods
kubectl get services
```

---

## 📊 Monitoring Setup

1. Prometheus scrapes metrics from the Flask app at `/metrics`
2. Grafana connects to Prometheus as a data source
3. Dashboards display: request rate, error rate, CPU/memory usage, incident count
4. Alert rules fire when error rate > threshold or pod is down

---

## 🔁 CI/CD Pipeline (Jenkins)

```
Stage 1: Checkout  →  Pull latest code from GitHub
Stage 2: Build     →  docker build -t incident-tracker .
Stage 3: Test      →  Run unit tests inside container
Stage 4: Push      →  Push image to Docker Hub
Stage 5: Deploy    →  kubectl apply -f k8s/ (zero-downtime rollout)
```

---
