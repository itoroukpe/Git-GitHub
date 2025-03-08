### **🔥 Git Hands-on Exercises with Solutions**  
These exercises will give your students practical experience with Git commands. Each exercise contains **instructions** followed by a **solution**.

---

## **💻 Exercise 1: Check Repository Status**  
### **Objective:** Learn how to check the status of the working directory.  

**🛠 Steps:**  
1. Open a terminal and navigate to a Git repository. If you don’t have one, create a new one:  
   ```sh
   mkdir my-git-project && cd my-git-project
   git init
   ```

2. Create a new file and check the Git status:  
   ```sh
   echo "Hello DevOps" > file1.txt
   git status
   ```

**✅ Expected Output:**  
Git should show `file1.txt` as an **untracked file**.

---

## **💻 Exercise 2: Stage a File for Commit**  
### **Objective:** Learn how to stage files using `git add`.  

**🛠 Steps:**  
1. Add the file to the staging area:  
   ```sh
   git add file1.txt
   ```

2. Check the Git status again:  
   ```sh
   git status
   ```

**✅ Expected Output:**  
The file should be marked as **staged**.

---

## **💻 Exercise 3: Unstage a File**  
### **Objective:** Learn how to unstage a file while keeping its changes.  

**🛠 Steps:**  
1. Unstage `file1.txt`:  
   ```sh
   git reset file1.txt
   ```

2. Check Git status again:  
   ```sh
   git status
   ```

**✅ Expected Output:**  
The file should move from **staged** to **modified**.

---

## **💻 Exercise 4: View Unstaged Changes**  
### **Objective:** Learn how to see changes made to files that are not yet staged.  

**🛠 Steps:**  
1. Modify `file1.txt`:  
   ```sh
   echo "Updated Content" >> file1.txt
   ```

2. Check the differences:  
   ```sh
   git diff
   ```

**✅ Expected Output:**  
Git should display the **changes** made in `file1.txt`.

---

## **💻 Exercise 5: View Staged Changes**  
### **Objective:** Learn how to see changes that are staged but not yet committed.  

**🛠 Steps:**  
1. Stage the file again:  
   ```sh
   git add file1.txt
   ```

2. View staged differences:  
   ```sh
   git diff --staged
   ```

**✅ Expected Output:**  
Git should show the **staged changes**.

---

## **💻 Exercise 6: Commit Changes**  
### **Objective:** Learn how to commit changes to the repository.  

**🛠 Steps:**  
1. Commit the staged changes:  
   ```sh
   git commit -m "Added file1.txt with updated content"
   ```

2. Check Git log:  
   ```sh
   git log --oneline
   ```

**✅ Expected Output:**  
The commit should be visible in the log.

---

## **💻 Exercise 7: Configure Git User Information**  
### **Objective:** Learn how to configure Git for personal use.  

**🛠 Steps:**  
1. Set up user details:  
   ```sh
   git config --global user.name "John Doe"
   git config --global user.email "johndoe@example.com"
   ```

2. Enable automatic command-line color formatting:  
   ```sh
   git config --global color.ui auto
   ```

3. Verify configuration:  
   ```sh
   git config --list
   ```

**✅ Expected Output:**  
Git should display the **configured username, email, and color settings**.

---

## **💻 Exercise 8: Initialize a Git Repository**  
### **Objective:** Learn how to initialize a Git repository.  

**🛠 Steps:**  
1. Create and initialize a new project:  
   ```sh
   mkdir my-new-project && cd my-new-project
   git init
   ```

2. Check the `.git` directory:  
   ```sh
   ls -la .git
   ```

**✅ Expected Output:**  
Git should initialize a new repository.

---

## **💻 Exercise 9: Clone a Repository**  
### **Objective:** Learn how to clone a remote repository.  

**🛠 Steps:**  
1. Clone an example GitHub repository:  
   ```sh
   git clone https://github.com/githubtraining/hellogitworld.git
   ```

2. Change into the cloned directory:  
   ```sh
   cd hellogitworld
   ```

3. List files to verify the clone:  
   ```sh
   ls
   ```

**✅ Expected Output:**  
The repository should be cloned successfully.

---

## **💻 Exercise 10: Create and Switch Branches**  
### **Objective:** Learn how to create and switch between branches.  

**🛠 Steps:**  
1. Create a new branch:  
   ```sh
   git branch feature-branch
   ```

2. Switch to the new branch:  
   ```sh
   git checkout feature-branch
   ```

3. Verify the active branch:  
   ```sh
   git branch
   ```

**✅ Expected Output:**  
A `*` should appear next to `feature-branch`.

---

## **💻 Exercise 11: Merge Branches**  
### **Objective:** Learn how to merge branches.  

**🛠 Steps:**  
1. Switch back to the `main` branch:  
   ```sh
   git checkout main
   ```

2. Merge `feature-branch` into `main`:  
   ```sh
   git merge feature-branch
   ```

3. Check commit history:  
   ```sh
   git log --oneline --graph --all
   ```

**✅ Expected Output:**  
The branch should be merged successfully.

---

## **💻 Exercise 12: View Commit History**  
### **Objective:** Learn how to view commit history.  

**🛠 Steps:**  
1. Run the following command:  
   ```sh
   git log
   ```

2. View a summarized version:  
   ```sh
   git log --oneline --graph --all
   ```

**✅ Expected Output:**  
A list of commits with branch structure should be displayed.

---

### **🚀 Summary of Commands Covered**
| **Command**             | **Purpose** |
|-------------------------|-------------|
| `git status`           | Check repository status |
| `git add [file]`       | Stage a file |
| `git reset [file]`     | Unstage a file |
| `git diff`             | Show unstaged changes |
| `git diff --staged`    | Show staged but uncommitted changes |
| `git commit -m ""`     | Commit staged changes |
| `git config --global`  | Configure Git settings |
| `git init`             | Initialize a Git repository |
| `git clone [url]`      | Clone a remote repository |
| `git branch`           | List branches |
| `git branch [name]`    | Create a new branch |
| `git checkout`         | Switch branches |
| `git merge [branch]`   | Merge a branch |
| `git log`              | View commit history |

---

### **💡 Next Steps**
✅ Implement these exercises in a **lab environment**  
✅ Use **GitHub Issues** to track progress  
✅ Expand to **GitHub Actions & CI/CD pipelines**  

