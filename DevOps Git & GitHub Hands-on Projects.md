Here’s a structured **hands-on project guide** for your **DevOps students** to gain practical experience with **Git and GitHub**. These exercises progress from **basic to advanced**, ensuring they build a solid foundation.

---

## **🚀 DevOps Git & GitHub Hands-on Projects**
### **Project 1: Git Basics - Local Repository Setup**
📌 **Objective:** Learn how to initialize, configure, and use Git locally.

#### **🛠️ Steps:**
1. **Install Git** (if not installed)
   ```sh
   sudo apt update && sudo apt install git -y  # Ubuntu
   brew install git  # Mac
   ```

2. **Configure Git**  
   ```sh
   git config --global user.name "Your Name"
   git config --global user.email "your-email@example.com"
   ```

3. **Initialize a Repository**
   ```sh
   mkdir my-first-repo && cd my-first-repo
   git init
   ```

4. **Create a file and commit it**
   ```sh
   echo "Hello DevOps" > readme.md
   git add readme.md
   git commit -m "Initial commit"
   ```

---

## **Project 2: Working with Branches & Merging**
📌 **Objective:** Learn branching, merging, and conflict resolution.

#### **🛠️ Steps:**
1. **Create a new branch**
   ```sh
   git branch feature-branch
   git checkout feature-branch
   ```

2. **Make changes in the new branch**
   ```sh
   echo "Feature Update" >> readme.md
   git add readme.md
   git commit -m "Added a new feature"
   ```

3. **Merge back into `main`**
   ```sh
   git checkout main
   git merge feature-branch
   ```

4. **Resolve conflicts if any**  
   - If Git shows merge conflicts, manually edit the conflicting file.
   - Use `git add <file>` to mark the conflict as resolved.
   - Commit the merge with `git commit -m "Resolved merge conflict"`.

---

## **Project 3: Collaborating with GitHub**
📌 **Objective:** Learn how to push code to GitHub and work with remote repositories.

#### **🛠️ Steps:**
1. **Create a GitHub Repository**
   - Go to [GitHub](https://github.com/)
   - Click **New Repository**, name it `my-devops-repo`, and create it.

2. **Connect Local Repo to GitHub**
   ```sh
   git remote add origin https://github.com/yourusername/my-devops-repo.git
   git branch -M main
   git push -u origin main
   ```

3. **Clone a Repository**
   ```sh
   git clone https://github.com/yourusername/my-devops-repo.git
   ```

---

## **Project 4: GitHub Pull Requests & Code Reviews**
📌 **Objective:** Learn how to work with pull requests and reviews.

#### **🛠️ Steps:**
1. **Fork a Repository on GitHub**
   - Go to a public repo, click `Fork`, and clone it.

2. **Make Changes & Push to a New Branch**
   ```sh
   git checkout -b bugfix
   echo "Bug fixed!" >> readme.md
   git add .
   git commit -m "Fixed a bug"
   git push origin bugfix
   ```

3. **Open a Pull Request (PR)**
   - Go to the repository on GitHub.
   - Click **Pull Requests** → **New Pull Request**.
   - Select `bugfix` as the source and `main` as the destination.
   - Click **Create Pull Request**.

4. **Request Code Reviews**
   - Assign reviewers and discuss suggested changes.

5. **Merge the PR**
   - Click **Merge Pull Request** once approved.

---

## **Project 5: Automating Workflows with GitHub Actions**
📌 **Objective:** Learn how to automate CI/CD pipelines using GitHub Actions.

#### **🛠️ Steps:**
1. **Create a `.github/workflows/ci.yml` file**
   ```yaml
   name: CI Pipeline

   on: push

   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - name: Checkout code
           uses: actions/checkout@v3

         - name: Set up Node.js
           uses: actions/setup-node@v3
           with:
             node-version: '18'

         - name: Run Tests
           run: echo "Running Tests..."
   ```

2. **Commit and Push**
   ```sh
   git add .github/workflows/ci.yml
   git commit -m "Added GitHub Actions CI pipeline"
   git push origin main
   ```

3. **Check Actions Tab on GitHub**
   - Navigate to **Actions** on your repository.
   - Verify the pipeline ran successfully.

---

## **🔥 Bonus Challenge: Deploying to AWS with GitHub Actions**
📌 **Objective:** Deploy a simple web app to **AWS EC2** using GitHub Actions.

#### **🛠️ Steps:**
1. **Launch an EC2 Instance** (Amazon Linux/Ubuntu).
2. **Install Git, Nginx, and Node.js**
   ```sh
   sudo apt update && sudo apt install git nginx nodejs -y
   ```
3. **Configure GitHub Actions to SSH into EC2**
   ```yaml
   - name: Deploy to EC2
     uses: appleboy/ssh-action@master
     with:
       host: ${{ secrets.EC2_HOST }}
       username: ubuntu
       key: ${{ secrets.SSH_PRIVATE_KEY }}
       script: |
         cd /var/www/myapp
         git pull origin main
         npm install
         pm2 restart myapp
   ```
4. **Commit and Push Code**
   ```sh
   git add .
   git commit -m "Setup AWS deployment pipeline"
   git push origin main
   ```

---

### **💡 Learning Outcomes**
✅ Understand Git fundamentals  
✅ Work with branches, commits, and pull requests  
✅ Collaborate using GitHub  
✅ Automate workflows with GitHub Actions  
✅ Deploy applications using CI/CD  
