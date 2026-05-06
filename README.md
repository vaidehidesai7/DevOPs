# Portfolio DevOps Project
**Module:** CSI_7_COD_2526 - Container Orchestration for DevOps  
**Student ID:** [4432496]

## Description
A cloud-native portfolio web application running on Nginx, containerized with Docker, and deployed via a Jenkins CI/CD pipeline to Kubernetes.

## Setup Instructions
1. **Clone the repository:**
   `git clone https://github.com/vaidehidesai7/DevOPs.git`
2. **Build Docker Image:**
   `docker build -t portfolio:v1 .`
3. **Run Locally:**
   `docker run -p 8081:80 portfolio:v1`
4. **Access the App:** 
   Open browser at `http://localhost:8081`

## CI/CD Pipeline
- **Source:** GitHub (main & develop branches)
- **CI Tool:** Jenkins
- **Orchestration:** Kubernetes
