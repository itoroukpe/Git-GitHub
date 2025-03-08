### **🚀 Real-World DevOps Projects Integrating Git with CI/CD, Jenkins, and Docker**

Here are **practical hands-on projects** for your **DevOps students** that integrate **Git, Jenkins, Docker, and CI/CD pipelines**. Each project includes **objectives, step-by-step exercises, and expected outcomes**.

---

## **🔥 Project 1: Version Control & CI/CD Pipeline with Jenkins**
📌 **Objective:**  
- Use **Git** for source control  
- Configure **Jenkins** for CI/CD  
- Automate builds, tests, and deployment  

### **🛠 Steps to Complete**
1. **Set up a GitHub Repository**  
   ```sh
   git init
   echo "Hello DevOps!" > index.html
   git add index.html
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/devops-pipeline.git
   git push -u origin main
   ```
   
2. **Install & Configure Jenkins on a Server**  
   ```sh
   sudo apt update && sudo apt install openjdk-11-jdk -y
   wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
   sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
   sudo apt update
   sudo apt install jenkins -y
   sudo systemctl start jenkins
   ```

3. **Create a Jenkins Job to Pull Code from GitHub**
   - Open Jenkins (`http://your-server-ip:8080`)
   - Install the **Git Plugin** (`Manage Jenkins -> Plugins`)
   - Create a **Freestyle Project**
   - Add `https://github.com/yourusername/devops-pipeline.git` in **Source Code Management**
   - Add a **Build Step**: `echo "Build successful"`

4. **Trigger Jenkins Pipeline on `git push`**
   - Go to `Manage Jenkins -> Configure Global Security`
   - Enable **GitHub Webhooks**
   - Set a webhook in GitHub:  
     - `Settings -> Webhooks -> Add Webhook`
     - Payload URL: `http://your-jenkins-server:8080/github-webhook/`
     - Content Type: `application/json`

🔹 **Expected Outcome:**  
✔️ Every time a commit is pushed to GitHub, **Jenkins will pull the latest code, build it, and execute tests**.

---

## **🔥 Project 2: Dockerized CI/CD Pipeline**
📌 **Objective:**  
- Automate Docker builds and deployments with GitHub & Jenkins.  

### **🛠 Steps to Complete**
1. **Set Up a GitHub Repository**  
   ```sh
   mkdir docker-ci-cd
   cd docker-ci-cd
   echo "FROM nginx:alpine" > Dockerfile
   git init
   git add Dockerfile
   git commit -m "Added Dockerfile"
   git remote add origin https://github.com/yourusername/docker-ci-cd.git
   git push -u origin main
   ```

2. **Install Docker on Jenkins Server**  
   ```sh
   sudo apt update
   sudo apt install docker.io -y
   sudo usermod -aG docker jenkins
   sudo systemctl restart jenkins
   ```

3. **Create a Jenkins Pipeline to Build & Push Docker Image**
   - **Create a New Pipeline Job**  
   - Use the following **Jenkinsfile**:
   ```groovy
   pipeline {
       agent any
       stages {
           stage('Checkout') {
               steps {
                   git 'https://github.com/yourusername/docker-ci-cd.git'
               }
           }
           stage('Build Docker Image') {
               steps {
                   sh 'docker build -t myrepo/myapp:latest .'
               }
           }
           stage('Push to Docker Hub') {
               steps {
                   withDockerRegistry([credentialsId: 'docker-hub-credentials', url: '']) {
                       sh 'docker push myrepo/myapp:latest'
                   }
               }
           }
       }
   }
   ```

4. **Push Code and Trigger Pipeline**
   ```sh
   git add .
   git commit -m "Updated Dockerfile"
   git push origin main
   ```
   - **Expected Output:** Jenkins builds and pushes the Docker image to Docker Hub.

🔹 **Expected Outcome:**  
✔️ Every GitHub push **triggers Jenkins to build and deploy a Docker container**.

---

## **🔥 Project 3: Deploying a Microservice with Kubernetes & GitOps**
📌 **Objective:**  
- Deploy a containerized app using **Kubernetes**  
- Automate deployments using **GitOps (ArgoCD / Flux)**  

### **🛠 Steps to Complete**
1. **Create a Kubernetes Cluster (Minikube)**
   ```sh
   minikube start
   ```

2. **Create a Deployment YAML**
   ```yaml
   apiVersion: apps/v1
   kind: Deployment
   metadata:
     name: myapp
   spec:
     replicas: 2
     selector:
       matchLabels:
         app: myapp
     template:
       metadata:
         labels:
           app: myapp
       spec:
         containers:
         - name: myapp
           image: myrepo/myapp:latest
           ports:
           - containerPort: 80
   ```
   ```sh
   kubectl apply -f deployment.yaml
   ```

3. **Set Up ArgoCD for GitOps**
   ```sh
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

4. **Connect ArgoCD to GitHub**
   - Add a **GitHub repo** in ArgoCD UI (`http://your-server-ip:8080/argocd/`)
   - Deploy new changes from GitHub automatically.

🔹 **Expected Outcome:**  
✔️ **Any push to GitHub updates the Kubernetes deployment automatically**.

---

## **🔥 Project 4: Automating Infrastructure with Terraform & GitHub Actions**
📌 **Objective:**  
- Use **Terraform** to provision AWS infrastructure.  
- Automate infrastructure deployments with **GitHub Actions**.

### **🛠 Steps to Complete**
1. **Create a Terraform Script**
   ```hcl
   provider "aws" {
     region = "us-east-1"
   }

   resource "aws_s3_bucket" "my_bucket" {
     bucket = "my-devops-bucket"
   }
   ```

2. **Set Up GitHub Actions for Terraform**
   - Create `.github/workflows/terraform.yml`
   ```yaml
   name: Terraform Deploy
   on: push

   jobs:
     deploy:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout code
           uses: actions/checkout@v2
         - name: Setup Terraform
           uses: hashicorp/setup-terraform@v1
         - name: Terraform Init
           run: terraform init
         - name: Terraform Apply
           run: terraform apply -auto-approve
   ```

3. **Push Code and Trigger Terraform Deployment**
   ```sh
   git add .
   git commit -m "Provision AWS S3 bucket with Terraform"
   git push origin main
   ```

🔹 **Expected Outcome:**  
✔️ **Terraform automatically provisions AWS infrastructure when a commit is pushed to GitHub**.

---

## **🔥 Summary of Key Learning Outcomes**
✅ **Jenkins + GitHub Webhooks** for automated builds  
✅ **Docker + CI/CD Pipelines** for containerized deployments  
✅ **GitOps (ArgoCD) + Kubernetes** for automated microservices  
✅ **Terraform + GitHub Actions** for infrastructure automation  

