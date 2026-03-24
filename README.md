# Flask To-Do App with Kubernetes & Monitoring

A professional, containerized To-Do application built with **Flask** and **MongoDB**, deployed on a high-availability **AWS EKS** cluster featuring automated self-healing, rolling updates, and real-time alerting.

---

## 🚀 Key Features

* **Multi-Tier Architecture**: Decoupled Flask frontend and MongoDB backend.
* **High Availability**: Configured with **3 replicas** and managed via **ReplicaSets** (Part 5).
* **Zero-Downtime Deployment**: Implemented **RollingUpdate** strategy for Version 2 (V2) deployment (Part 6).
* **Self-Healing**: Integrated **Liveness** and **Readiness** probes to automatically detect and recover from failures (Part 7).
* **Cloud Infrastructure**: Fully deployed on **AWS EKS** with an **Elastic Load Balancer (ELB)** for external access (Part 4).
* **Observability Pipeline**: Real-time cluster monitoring using **Prometheus** and automated **Slack** notifications via Alertmanager (Part 8).

---

## 📂 Project Structure

```text
.
├── Web/
│   ├── app.py              # Flask Application (Updated to V2)
│   ├── Dockerfile          # Container definition
│   └── requirements.txt    # Python dependencies
├── k8s/
│   ├── flask-stack.yaml    # Flask Deployment, Service (LoadBalancer) & Probes
│   ├── mongo-stack.yaml    # MongoDB Deployment & ClusterIP Service
│   └── alert-values.yaml   # Prometheus Alertmanager Slack configuration
└── README.md
