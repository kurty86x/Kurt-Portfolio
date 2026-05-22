# 📝 Overview
This project demonstrates how I deployed a beginner‑level Kubernetes lab using Minikube (and optionally k3s) to learn how containerized applications run in a cluster.

The goal was to understand Deployments, Services, Pods, Namespaces, scaling, and basic security concepts — all foundational DevSecOps and cloud‑native skills.

--- 

### 🎯 Objectives
- Deploy a local Kubernetes cluster
- Create Deployments and Services
- Understand Pods, ReplicaSets, and scaling
- Expose applications using NodePort
- Practice rolling updates and rollbacks
- Explore basic pod security settings

---

### 🏗️ Lab Environment
- Minikube installed on Linux/Windows
- kubectl CLI
- Docker installed (Minikube uses it internally)
- Simple containerized web app

---

## 🚀 Starting the Cluster

### Start Minikube
```
Command:
minikube 
```

### Check cluster status
```
Command:
kubectl get nodes
```
You sould see **1 Ready node**


## 📁 Project Structure
```Folder Structure
kubernetes-lab/
│── deployments/
│     └── web-deployment.yaml
│── services/
│     └── web-service.yaml
│── namespaces/
│     └── dev-namespace.yaml
└── docs/
```

## 🧱 Creating a Namespace

dev-namespace.yaml
```dev-namespace.yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```
**Apply it:**
```
Command:
kubectl apply -f namespaces/dev-namespace.yaml
```

### 📦 Deployment
web-deployment.yaml
```Deployment
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-deployment
  namespace: dev
spec:
  replicas: 2
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: web
        image: nginx:latest
        ports:
        - containerPort: 80
```
**Apply it:**
```
Command:
kubectl apply -f deployments/web-deployment.yaml
```
**Check pods:**
```
Command:
kubectl get pods -n dev
```


## 🌐 Exposing the App (NodePort)
web-service.yaml
```web-service.yaml
apiVersion: v1
kind: Service
metadata:
  name: web-service
  namespace: dev
spec:
  type: NodePort
  selector:
    app: web
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080
```

**Apply it:**
```
Command:
kubectl apply -f services/web-service.yaml
```
**Access the app:**
```
Command:
minikube service web-service -n dev
```


## 🔄 Rolling Updates & Rollbacks
### Update the image:
```
Command:
kubectl set image deployment/web-deployment web=nginx:1.25 -n dev
```

### Check rollout
```Check rollout
Command:
kubectl rollout status deployment/web-deployment -n dev
```

### Rollback
```Rollback
Command:
kubectl rollout undo deployment/web-deployment -n dev
```

---

## 🔐 Basic Pod Security Practices
- Use official images
- Limit container privileges
- Add resource limits
- Use namespaces for separation

**Example resource limits**

resource_limits.yml
```
resources:
  limits:
    cpu: "500m"
    memory: "256Mi"
```


---

## 🧪 Validation Checklist
- Namespace created
- Deployment running with 2 replicas
- Service exposes the app on NodePort
- App reachable in browser
- Rolling update succeeds
- Rollback works correctly

---

## 🛠️ Troubleshooting
- **Pods stuck in CrashLoopBackOff**
  ```
  Command:
  kubectl logs pod-name -n dev
  ```
- **Service not reachable  **  
  Check NodePort:
  ```
  Command:
  kubectl get svc -n dev
  ```
- **Image pull errors** 

  Ensure image exists or use nginx:latest.

---

## 📘 What I Learned
- How Kubernetes organizes workloads (Pods, Deployments, Services)
- How to deploy and scale applications
- How to expose apps using NodePort
- How rolling updates and rollbacks work
- How namespaces help organize environments