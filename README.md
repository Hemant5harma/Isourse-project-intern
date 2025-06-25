# Isourse Project Intern - DevOps CI/CD Pipeline

A complete DevOps CI/CD pipeline implementation using Jenkins for automation and Google Kubernetes Engine (GKE) for cloud-native deployment.

## 📋 Project Overview

This project demonstrates a production-ready CI/CD pipeline that automates the entire software delivery process from code commit to deployment. It showcases modern DevOps practices using containerization, orchestration, and continuous integration/deployment.

## 🏗️ Architecture

The project implements a comprehensive CI/CD workflow:

1. **Source Control**: GitHub repository hosting
2. **CI/CD Automation**: Jenkins pipeline with automated triggers
3. **Containerization**: Docker for application packaging
4. **Container Registry**: Docker Hub for image storage
5. **Orchestration**: Kubernetes (GKE) for container deployment
6. **Cloud Platform**: Google Cloud Platform (GCP)

## 🛠️ Technologies Used

- **Jenkins**: CI/CD automation server
- **Docker**: Application containerization
- **Kubernetes**: Container orchestration
- **Google Cloud Platform (GCP)**: Cloud infrastructure
- **Google Kubernetes Engine (GKE)**: Managed Kubernetes service
- **Docker Hub**: Container image registry
- **Nginx**: Web server for serving static content
- **HTML/CSS**: Frontend presentation layer

## 📁 Project Structure

```
├── Dockerfile              # Container build instructions
├── deployment.yml           # Kubernetes deployment configuration
├── service.yml             # Kubernetes service configuration
├── index.html              # Application frontend
├── jenkins/
│   └── jenkins-pipeline.yml # Jenkins pipeline configuration
└── README.md               # Project documentation
```

## 🚀 CI/CD Pipeline Flow

### Pipeline Stages

1. **Git Checkout**: Clones the latest code from the main branch
2. **Test**: Runs application tests (currently placeholder)
3. **Build Docker Image**: Creates containerized application
4. **Push Docker Image**: Uploads image to Docker Hub registry
5. **Authenticate with GKE**: Sets up GCP credentials and cluster access
6. **Deploy to Kubernetes**: Applies deployment and service configurations

### Pipeline Configuration

The Jenkins pipeline (`jenkins/jenkins-pipeline.yml`) includes:

- **Environment Variables**:
  - `PROJECT_ID`: GCP project identifier
  - `CLUSTER_NAME`: GKE cluster name
  - `CLUSTER_ZONE`: GCP zone for the cluster

- **Credentials Management**:
  - Docker Hub credentials (`docker-cred`)
  - GKE service account credentials (`gke-cred`)

- **Email Notifications**: Automated success/failure notifications

## 🐳 Docker Configuration

The application uses Nginx as the web server:

```dockerfile
FROM nginx:latest
WORKDIR /usr/share/nginx/html
COPY . .
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## ☸️ Kubernetes Deployment

### Deployment Specification
- **Replicas**: 2 instances for high availability
- **Image**: `hemanthub/devops-intern-project:latest`
- **Port**: 80 (HTTP)

### Service Configuration
- **Type**: LoadBalancer for external access
- **Port Mapping**: 80:80
- **Selector**: Routes traffic to nginx-app pods

## 🔧 Setup Instructions

### Prerequisites

1. **Jenkins Server** with required plugins:
   - Docker Pipeline
   - Kubernetes CLI
   - Email Extension

2. **GCP Account** with:
   - GKE cluster created
   - Service account with appropriate permissions
   - Project ID configured

3. **Docker Hub Account** for image registry

### Configuration Steps

1. **Clone Repository**:
   ```bash
   git clone https://github.com/Hemant5harma/Isourse-project-intern.git
   ```

2. **Configure Jenkins Credentials**:
   - Add Docker Hub credentials as `docker-cred`
   - Add GCP service account key as `gke-cred`

3. **Create Jenkins Pipeline**:
   - Create new pipeline job
   - Point to `jenkins/jenkins-pipeline.yml`
   - Configure webhook for automated triggers

4. **Deploy to Kubernetes**:
   ```bash
   kubectl apply -f deployment.yml
   kubectl apply -f service.yml
   ```

## 📊 Monitoring and Troubleshooting

### Health Checks
```bash
# Check pod status
kubectl get pods

# View pod logs
kubectl logs deployment/nginx-app

# Check service status
kubectl get services
```

### Common Issues

- **Image Pull Errors**: Verify Docker Hub credentials and image tags
- **Deployment Failures**: Check GKE cluster permissions and resource quotas

## 🎯 Key Features

- ✅ Automated CI/CD pipeline
- ✅ Container-based deployment
- ✅ Kubernetes orchestration
- ✅ Cloud-native architecture
- ✅ Automated notifications
- ✅ Scalable infrastructure
- ✅ Production-ready configuration


## 📚 Additional Resources

- [Jenkins Documentation](https://www.jenkins.io/doc/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Google Cloud GKE](https://cloud.google.com/kubernetes-engine)

---
