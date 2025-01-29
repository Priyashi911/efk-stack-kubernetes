# EFK Stack for Kubernetes | Elasticsearch, Fluent Bit & Kibana
🚀 EFK Stack for Kubernetes | A centralized log monitoring solution using Elasticsearch, Fluent Bit, and Kibana to collect, process, and visualize logs from Kubernetes workloads. Perfect for real-time log aggregation, troubleshooting, and observability. 🔥

## 📌 Introduction
This repository contains a fully functional **EFK Stack (Elasticsearch, Fluent Bit, Kibana)** deployment on **Kubernetes**. The EFK stack is widely used for **centralized logging, log aggregation, and monitoring** in Kubernetes environments.

## 🚀 Features
- **Elasticsearch**: Stores and indexes logs efficiently.
- **Fluent Bit**: Collects and forwards container logs to Elasticsearch.
- **Kibana**: Provides a user-friendly interface for log visualization.
- **Kubernetes Deployments**: YAML manifests for easy deployment.
- **Persistent Storage**: Ensures logs are not lost after pod restarts.

## 📂 Project Structure
```
├── elasticsearch-kibana
│   ├── es-pvolume.yaml         # PersistentVolume for Elasticsearch
│   ├── es-service.yaml         # Service to expose Elasticsearch
│   ├── es-statefulset.yaml     # StatefulSet deployment for Elasticsearch
│   ├── kibana-deployment.yaml  # Kibana Deployment
│   ├── kibana-service.yaml     # Service to expose Kibana
│
├── event-generator
│   ├── fluent-bit-configmap.yaml  # ConfigMap for Fluent Bit configuration
│   ├── fluent-bit.yaml            # DaemonSet deployment for Fluent Bit
│
├── nginx
│   ├── nginx-deployment.yaml  # Deploys an Nginx pod for testing logs
│   ├── nginx-service.yaml     # Exposes the Nginx service
│
├── python-simple
│   ├── deployment.yaml  # Deploys a simple Python application
│
└── README.md  # Project documentation
```

## ⚡ Prerequisites
- Kubernetes Cluster (Minikube, K3s, EKS, GKE, AKS, etc.)
- `kubectl` installed and configured
- Helm (Optional, for managing Elasticsearch)

## 🚀 Deployment Steps

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/efk-stack-kubernetes.git
cd efk-stack-kubernetes
```

### 2️⃣ Deploy Elasticsearch & Kibana
```bash
kubectl apply -f elasticsearch-kibana/
```
🔹 **Verify Pods & Services:**
```bash
kubectl get pods -n kube-system | grep elasticsearch
kubectl get svc -n kube-system | grep kibana
```

### 3️⃣ Deploy Fluent Bit (Log Collector)
```bash
kubectl apply -f event-generator/
```
🔹 **Check Fluent Bit logs:**
```bash
kubectl logs -l app=fluent-bit -n kube-system
```

### 4️⃣ Deploy Nginx & Python App (For Log Testing)
```bash
kubectl apply -f nginx/
kubectl apply -f python-simple/
```

### 5️⃣ Access Kibana Dashboard
1. Get the **Kibana NodePort**:
```bash
kubectl get svc | grep kibana
```
2. Open in Browser: `http://<NODE-IP>:<KIBANA-PORT>`
3. Configure **Elasticsearch URL**: `http://elasticsearch:9200`

## 📊 Log Visualization in Kibana
1. **Go to** `Discover` section in Kibana.
2. Select **Index Pattern**: `kubernetes-logs-*`.
3. Start **exploring logs in real-time**!

## 🎯 Use Cases
✅ Kubernetes log aggregation  
✅ Real-time monitoring and analysis  
✅ Debugging and troubleshooting  
✅ Security and compliance logging  

## 🛠️ Customization
- Modify `fluent-bit-configmap.yaml` to filter logs.
- Change `es-statefulset.yaml` to scale Elasticsearch.
- Update `kibana-deployment.yaml` to enable authentication.

## 🔥 Contributing
Feel free to **fork** this repo, create a new branch, and submit a **Pull Request (PR)**. Contributions are welcome! 🚀

## 📜 License
This project is licensed under the **MIT License**. Feel free to use and modify it.

---

🚀 **Happy Logging with EFK Stack!** 🎯


