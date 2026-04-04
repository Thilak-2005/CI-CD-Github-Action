# CI/CD Pipeline with AWS EKS, ECR & GitHub Actions

## Project Overview

This project demonstrates a complete **CI/CD pipeline** where application changes pushed to GitHub are automatically built, containerized, and deployed to AWS EKS.

---

## Architecture

```
Developer → GitHub → GitHub Actions → Docker → AWS ECR → AWS EKS → LoadBalancer → Users
```

---

## Tech Stack

* **Cloud**: AWS (EKS, ECR, ELB)
* **CI/CD**: GitHub Actions
* **Containerization**: Docker
* **Orchestration**: Kubernetes (EKS)
* **Language**: Python (Flask)

---

## Project Structure

```
cicd-project/
│
├── app/
│   ├── app.py
│   ├── requirements.txt
│   └── Dockerfile
│
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
│
└── .github/
    └── workflows/
        └── deploy.yml
```

---

## 🚀 CI/CD Workflow

1. Developer pushes code to GitHub
2. GitHub Actions pipeline triggers
3. Docker image is built
4. Image is pushed to AWS ECR
5. Kubernetes deployment is updated in EKS
6. Application is exposed via LoadBalancer

---

## 🐳 Docker Build & Push

```bash
docker build -t cicd-app ./app
docker tag cicd-app:latest <ECR_URI>:latest
docker push <ECR_URI>:latest
```

---

## ☸️ Kubernetes Deployment

```bash
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml
```

---

## 🌍 Access Application

```bash
kubectl get svc
```

Open in browser:

```
http://<EXTERNAL-IP>
```

---

## 🧪 CI/CD Test

1. Modify `app.py`
2. Push changes:

```bash
git add .
git commit -m "update"
git push
```

3. Pipeline runs automatically
4. Application updates in real-time

---

## 📸 Screenshots

### 🔹 1. GitHub Actions Pipeline

![Pipeline Screenshot](screenshots/pipeline.png)

### 🔹 2. EKS Pods Running

![Pods Screenshot](screenshots/pods.png)

### 🔹 3. LoadBalancer Output

![Service Screenshot](screenshots/service.png)

### 🔹 4. Application Output in Browser

![App Screenshot](screenshots/app.png)

---

## 🔐 Security Note

* AWS credentials are stored securely using GitHub Secrets
* No sensitive data is hardcoded in the repository

---

## 🧠 Key Learnings

* End-to-end CI/CD pipeline implementation
* Docker containerization
* Kubernetes deployment on AWS EKS
* Automated deployment using GitHub Actions

---

