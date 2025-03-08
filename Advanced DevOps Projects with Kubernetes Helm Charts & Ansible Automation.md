### **🚀 Advanced DevOps Projects with Kubernetes Helm Charts & Ansible Automation**

Here are **practical hands-on projects** that incorporate **Kubernetes Helm charts and Ansible** for advanced **DevOps automation**. Each project includes objectives, step-by-step exercises, and expected outcomes.

---

## **🔥 Project 1: Deploying a Microservice with Helm Charts**
📌 **Objective:**  
- Use **Helm** to deploy a microservice in Kubernetes.  
- Parameterize configurations using **Helm templates**.  
- Automate deployments using **GitOps (ArgoCD or Flux)**.

### **🛠 Steps to Complete**
1️⃣ **Install Helm**
   ```sh
   curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
   ```

2️⃣ **Create a Helm Chart for an Nginx Microservice**
   ```sh
   helm create my-nginx
   cd my-nginx
   ```

3️⃣ **Modify `values.yaml` to Customize Deployment**
   ```yaml
   replicaCount: 2

   image:
     repository: nginx
     tag: "latest"
     pullPolicy: IfNotPresent

   service:
     type: LoadBalancer
     port: 80
   ```

4️⃣ **Install Helm Chart in Kubernetes**
   ```sh
   kubectl create namespace dev
   helm install nginx-release my-nginx --namespace dev
   ```

5️⃣ **Upgrade Helm Chart with Changes**
   ```sh
   helm upgrade nginx-release my-nginx --namespace dev
   ```

6️⃣ **Roll Back to a Previous Version**
   ```sh
   helm rollback nginx-release 1
   ```

🔹 **Expected Outcome:**  
✔️ The microservice is **easily managed and upgraded** using Helm.

---

## **🔥 Project 2: Kubernetes GitOps Workflow with ArgoCD and Helm**
📌 **Objective:**  
- Automate **Kubernetes deployments** using **GitOps**.  
- Use **ArgoCD** to track **Helm-based applications** in GitHub.

### **🛠 Steps to Complete**
1️⃣ **Install ArgoCD**
   ```sh
   kubectl create namespace argocd
   kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
   ```

2️⃣ **Login to ArgoCD**
   ```sh
   kubectl port-forward svc/argocd-server -n argocd 8080:443
   argocd login localhost:8080 --username admin --password <password>
   ```

3️⃣ **Deploy a Helm App with ArgoCD**
   - Create a GitHub repo with the Helm chart (`my-nginx`).
   - Connect the repo to **ArgoCD UI**.
   - Click `Sync` to deploy **automatically from GitHub**.

🔹 **Expected Outcome:**  
✔️ **GitHub commits auto-deploy to Kubernetes** with Helm + ArgoCD.

---

## **🔥 Project 3: Automating Server Provisioning with Ansible**
📌 **Objective:**  
- Automate **Linux server provisioning** using Ansible.  
- Deploy a **Nginx Web Server** using Ansible Playbooks.

### **🛠 Steps to Complete**
1️⃣ **Install Ansible on Your Workstation**
   ```sh
   sudo apt update
   sudo apt install ansible -y
   ```

2️⃣ **Set Up an Ansible Inventory (`inventory.ini`)**
   ```ini
   [webservers]
   server1 ansible_host=192.168.1.100 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
   ```

3️⃣ **Create an Ansible Playbook (`nginx-playbook.yml`)**
   ```yaml
   - name: Install and Configure Nginx
     hosts: webservers
     become: yes
     tasks:
       - name: Install Nginx
         apt:
           name: nginx
           state: present

       - name: Start Nginx Service
         service:
           name: nginx
           state: started
           enabled: yes

       - name: Copy Custom Index.html
         copy:
           src: index.html
           dest: /var/www/html/index.html
   ```

4️⃣ **Run the Ansible Playbook**
   ```sh
   ansible-playbook -i inventory.ini nginx-playbook.yml
   ```

🔹 **Expected Outcome:**  
✔️ Nginx is installed and configured **automatically on all servers**.

---

## **🔥 Project 4: Ansible + Docker: Automate Container Deployment**
📌 **Objective:**  
- Use **Ansible** to deploy **Docker containers** on multiple servers.  
- Automate the **entire container lifecycle**.

### **🛠 Steps to Complete**
1️⃣ **Install Docker on Remote Hosts using Ansible**
   ```yaml
   - name: Install Docker
     hosts: webservers
     become: yes
     tasks:
       - name: Install prerequisites
         apt:
           name:
             - apt-transport-https
             - ca-certificates
             - curl
             - software-properties-common
           state: present

       - name: Add Docker GPG key
         shell: curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

       - name: Install Docker
         apt:
           name: docker.io
           state: present
   ```

2️⃣ **Deploy an Nginx Container with Ansible**
   ```yaml
   - name: Deploy Nginx in Docker
     hosts: webservers
     become: yes
     tasks:
       - name: Run Nginx container
         docker_container:
           name: nginx
           image: nginx:latest
           state: started
           ports:
             - "80:80"
   ```

3️⃣ **Run the Playbook to Automate Deployment**
   ```sh
   ansible-playbook -i inventory.ini deploy-docker.yml
   ```

🔹 **Expected Outcome:**  
✔️ Docker + Nginx **auto-deploys across multiple servers**.

---

## **🔥 Project 5: CI/CD Pipeline with Ansible and Jenkins**
📌 **Objective:**  
- Use **Jenkins** to trigger **Ansible Playbooks**.  
- Automate **continuous deployment**.

### **🛠 Steps to Complete**
1️⃣ **Create a Jenkins Job with Ansible Execution**
   - Install **Ansible Plugin** in Jenkins.
   - Add an **Ansible Playbook Step**:
     ```sh
     ansible-playbook -i inventory.ini deploy-docker.yml
     ```

2️⃣ **Trigger Jenkins on GitHub Push**
   - Configure **GitHub Webhooks**:
     - Payload URL: `http://jenkins-server:8080/github-webhook/`
   - Now, when you **push a change to GitHub**, Jenkins runs **Ansible to update servers**.

🔹 **Expected Outcome:**  
✔️ **Automated deployments** using **GitHub, Jenkins, and Ansible**.

---

## **🔥 Bonus: Helm + Ansible + Terraform for Full Automation**
📌 **Objective:**  
- Use **Terraform** to provision Kubernetes.  
- Deploy **Helm charts** using **Ansible**.

### **🛠 Steps to Complete**
1️⃣ **Create Terraform Configuration for Kubernetes**
   ```hcl
   provider "aws" {
     region = "us-east-1"
   }

   resource "aws_eks_cluster" "eks" {
     name = "devops-cluster"
   }
   ```

2️⃣ **Use Ansible to Deploy Helm Apps**
   ```yaml
   - name: Deploy Helm Charts
     hosts: localhost
     tasks:
       - name: Install Nginx using Helm
         command: helm install my-nginx stable/nginx
   ```

3️⃣ **Run Terraform & Ansible**
   ```sh
   terraform apply -auto-approve
   ansible-playbook deploy-helm.yml
   ```

🔹 **Expected Outcome:**  
✔️ **Cloud-native Kubernetes deployment automated end-to-end**.

---

## **🔥 Summary of Key Learning Outcomes**
✅ **Helm for Kubernetes deployments**  
✅ **GitOps with ArgoCD for automated updates**  
✅ **Ansible for server & container automation**  
✅ **CI/CD with Jenkins + Ansible**  
✅ **Terraform for Infrastructure as Code (IaC)**  

