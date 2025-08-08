# 🐳 Dockerized Microservices App with Helm & ArgoCD (GitOps)

A complete DevOps pipeline for deploying a multi-service web application using Docker, Kubernetes, Helm, and ArgoCD.

---

## 🚀 Features

* **Containerization:** Docker for all services
* **Orchestration:** Kubernetes for scalable deployments
* **Packaging:** Helm charts for easy configuration
* **Continuous Delivery:** GitOps workflow with ArgoCD

---

## 🛠️ Tech Stack

| Layer         | Technology         |
| ------------- | ------------------ |
| Frontend      | HTML + NGINX       |
| Backend       | Flask (Python) API |
| Database      | PostgreSQL         |
| Container     | Docker             |
| Orchestration | Kubernetes         |
| GitOps        | Helm + ArgoCD      |

---

## 📁 Project Structure

```
realsahilthakur-dockerized-microservices-app/
├── README.md                         # This file
├── docker-compose.yml                # Docker Compose for local development
├── docker-stack.yml                  # Docker Stack for Docker Swarm deployment
├── BACKEND/                          # Backend service (Python Flask)
│   ├── app.py                        # Flask application code
│   ├── Dockerfile                    # Dockerfile for backend image
│   └── requirements.txt              # Python dependencies
├── FRONTEND/                         # Frontend service (Nginx serving static HTML)
│   ├── default.conf                  # Nginx configuration
│   ├── Dockerfile                    # Dockerfile for frontend image
│   └── index.html                    # Static HTML content
└── helm-chart/                       # Helm chart for Kubernetes deployment
    ├── Chart.yaml                    # Helm chart metadata
    ├── values.yaml                   # Default values for Helm chart
    └── templates/                    # Kubernetes resource templates
        ├── argocd-app.yaml           # ArgoCD Application definition
        ├── backend-deployment.yaml   # Kubernetes Deployment for backend
        ├── backend-service.yaml      # Kubernetes Service for backend
        ├── db-deployment.yaml        # Kubernetes Deployment for database
        ├── db-service.yaml           # Kubernetes Service for database
        ├── frontend-deployment.yaml  # Kubernetes Deployment for frontend
        └── frontend-service.yaml     # Kubernetes Service for frontend
```

🏗️ Local Development with Docker Compose

1\. \*\*Build and run all services:\*\*

`docker-compose up --build`

2. **Access frontend in browser:**

`http://localhost:8080`

3. **Stop services:**

`docker-compose down`

---

## ☸️ Kubernetes Deployment with Helm

1. **Create namespace (optional):**

`kubectl create ns microservices`

2. **Deploy with Helm:**

`helm install microservices-app ./helm-chart -n microservices`

3. **Upgrade / update deployment:**

`helm upgrade microservices-app ./helm-chart -n microservices`

---

## 🚀 Continuous Delivery with Argo CD (GitOps)

1. **Install Argo CD:**

`kubectl create ns argocd`

` kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argocd/stable/manifests/install.yaml`

2. **Port-forward Argo CD server:**

`kubectl port-forward svc/argocd-server -n argocd 8080:443`

3. **Login to Argo CD CLI:**

`argocd login localhost:8080 --insecure`

4. **Add your private GitHub repo to Argo CD:**

`argocd repo add https://github.com/realsahilthakur/dockerized-microservices-app.git --username <your-username> --password <Personal-access-token>`

5. **Create and sync app (or let it auto-sync):**

`argocd app sync microservices-app`

---


## 🙌 Author

**Sahil Thakur** & **Sneha Kaimal**


```DevOps | Kubernetes | CI/CD | GitOps | Python```

---

## 🏁 License

This project is licensed under the MIT License.
