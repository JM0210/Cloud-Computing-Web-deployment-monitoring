Flask To-Do App with Kubernetes & Monitoring
A full-stack, containerized To-Do application built with Flask and MongoDB, deployed on a high-availability AWS EKS cluster with automated monitoring and alerting.

🚀 Features
Containerization: Multi-tier architecture using Docker.

Orchestration: Managed by Kubernetes (Local Minikube & Cloud AWS EKS).

High Availability: Configured with 3 replicas and self-healing ReplicaSets.

Zero-Downtime Updates: Implemented using RollingUpdate strategy (V2 Deployment).

Self-Healing: Integrated Liveness and Readiness probes to monitor container health.

Cloud Networking: Accessible via AWS Elastic Load Balancer (ELB).

Observability: Real-time monitoring with Prometheus and automated Slack alerting.

🛠️ Kubernetes Deployment Steps
1. Deploy the Application Stack
Apply the configurations to your cluster:

Bash
kubectl apply -f k8s/mongo-stack.yaml
kubectl apply -f k8s/flask-stack.yaml
2. Verify the Status
Check the status of Pods, Services, and ReplicaSets:

Bash
kubectl get pods
kubectl get svc
kubectl get rs
3. Accessing the App
For AWS EKS, retrieve the external DNS name:

Bash
kubectl get service flask-service
🔍 Reliability & Monitoring (Advanced)
Self-Healing & Probes
The application includes Liveness and Readiness probes. If a container becomes unresponsive or the Flask service fails, Kubernetes automatically restarts the pod.

Observation: During testing, a misconfigured port (8000) triggered a CrashLoopBackOff, which was successfully detected and managed by the cluster.

Rolling Updates
Deployed Version 2 of the app using a rolling strategy:

Bash
# Update the image in flask-stack.yaml to :v2
kubectl apply -f k8s/flask-stack.yaml
kubectl rollout status deployment/flask-app
Alerting Pipeline
Monitoring is powered by the Prometheus stack. Alertmanager is configured to send notifications to a Slack channel (#k8s) whenever critical issues (like PodCrashLoopBackOff) are detected.

Security Note: Sensitive credentials (like Slack Webhooks) are managed via placeholders in this repository to follow DevSecOps best practices.

🛠️ Tech Stack
Backend: Python Flask

Database: MongoDB

Infrastructure: Kubernetes (EKS), AWS

Monitoring: Prometheus, Alertmanager

CI/CD & DevOps: Docker, Git, Slack Integration
