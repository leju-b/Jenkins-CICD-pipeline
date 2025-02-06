# 🚀 Jenkins CI/CD Pipeline for a Spring Boot Application

![Screenshot 2023-03-28 at 9 38 09 PM](https://user-images.githubusercontent.com/43399466/228301952-abc02ca2-9942-4a67-8293-f76647b6f9d8.png)

## 📌 Introduction
This repository contains a **fully automated CI/CD pipeline** for a **Java Spring Boot** application, integrating **Jenkins, Docker, SonarQube, Kubernetes, and ArgoCD**. The pipeline ensures automated **code quality checks, containerization, and deployment** to a Kubernetes cluster.

A huge thanks to **Abhishek Veeramalla** for his insightful YouTube videos (**DevOps: Zero to Hero**), which provided the foundation for this project. His content has been invaluable in understanding and implementing this pipeline.

---

## 📜 Features
- ✅ **Automated Build & Test** using **Jenkins & Maven**
- ✅ **Code Quality Analysis** with **SonarQube**
- ✅ **Containerization** using **Docker**
- ✅ **Image Push to Docker Hub**
- ✅ **Automated Deployment** to **Kubernetes** via **ArgoCD**

---

## ⚡ Technologies Used
- **Java Spring Boot**
- **Maven**
- **Jenkins**
- **SonarQube**
- **Docker**
- **Kubernetes (Minikube)**
- **ArgoCD**
- **GitHub Actions (Optional)**

---

## 🛠️ Setup & Installation

### 1️⃣ Clone the Repository
```sh
 git clone https://github.com/your-username/your-repo.git
 cd your-repo
```

### 2️⃣ Install Dependencies
Ensure **Java, Maven, and Docker** are installed:
```sh
java -version
mvn -version
docker --version
```

### 3️⃣ Run the Application Locally
```sh
mvn clean package
java -jar target/spring-boot-web.jar
```
Access the app at: **http://localhost:8080**

### 4️⃣ Run with Docker
```sh
docker build -t your-dockerhub-username/ultimate-cicd-pipeline:v1 .
docker run -d -p 8010:8080 your-dockerhub-username/ultimate-cicd-pipeline:v1
```
Access the app at: **http://localhost:8010**

---

## 🔧 Jenkins Pipeline Setup
1. Install required **Jenkins plugins**:
   - Pipeline, Docker Pipeline, SonarQube Scanner, GitHub Integration, Kubernetes CLI
2. Add **SonarQube credentials** to Jenkins.
3. Add **Docker Hub credentials** to Jenkins.
4. Create a **Jenkins pipeline** with this `Jenkinsfile`:

## 🚀 Deployment with Kubernetes & ArgoCD
1. **Ensure Minikube is running**:
   ```sh
   minikube start --driver=docker
   ```
2. **Install & configure ArgoCD**:
   ```sh
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```
3. **Expose ArgoCD dashboard**:
   ```sh
   kubectl port-forward svc/argocd-server -n argocd 8080:443
   ```
   Access **ArgoCD UI** at: **http://localhost:8080**

4. **Sync application using ArgoCD UI** or CLI:
   ```sh
   argocd login localhost:8080 --username admin --password <YOUR_PASSWORD>
   ```
   ```sh
   argocd app sync springboot-app
   ```
5. **Find the running application**:
   ```sh
   minikube service springboot-app --url
   ```

---

## 🐞 Debugging & Troubleshooting
- **Jenkins Pipeline Errors**: Check logs under **Build History**.
- **SonarQube Issues**: Ensure **SonarQube URL and token** are correctly set in Jenkins.
- **Docker Push Failures**: Verify **Docker Hub credentials** and login.
- **Kubernetes Issues**: Check pod status:
  ```sh
  kubectl get pods -n default
  ```
- **ArgoCD Sync Failures**: View ArgoCD events:
  ```sh
  kubectl get events -n argocd
  ```

---

## 🎯 Future Enhancements
✅ Implement **GitHub Actions** for additional CI/CD flexibility.  
✅ Add **Slack notifications** for Jenkins pipeline results.  
✅ Deploy using **Helm charts** for better Kubernetes management.  
✅ Implement **Infrastructure as Code (Terraform)** for automated cloud setup.  

---

## 🤝 Credits & Acknowledgment
This project was inspired by **@Abhishek Veeramalla's** amazing DevOps tutorials. His **YouTube series** and **GitHub repository (Jenkins-Zero-To-Hero)** provided me with **clear-cut knowledge** to implement this pipeline successfully. 🙌

If you're learning **DevOps**, I highly recommend his content! 🔥

---

## 📢 Let's Connect!
If you found this project useful, let's connect on **[LinkedIn](https://linkedin.com/in/your-profile)**! 🚀

---

### 🔥 Made with ❤️ & DevOps Passion!



    7. Run the Jenkins pipeline:
       7.1 Trigger the Jenkins pipeline to start the CI/CD process for the Java application.
       7.2 Monitor the pipeline stages and fix any issues that arise.

This end-to-end Jenkins pipeline will automate the entire CI/CD process for a Java application, from code checkout to production deployment, using popular tools like SonarQube, Argo CD, Helm, and Kubernetes.
