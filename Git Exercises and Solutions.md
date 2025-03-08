Here are **exercises and solutions** for each of the **Git commands** you listed, ensuring hands-on practice for your DevOps students.

---

## **🚀 Git Exercises and Solutions**

### **1️⃣ `git log` - Show commit history for the current branch**
📌 **Exercise:**  
- Clone any existing Git repository or initialize a new one.
- Create multiple commits with changes.
- Run `git log` to check the commit history.

🛠 **Solution:**
```sh
git log
```
This displays all commits on the currently active branch with details like author, date, and commit message.

---

### **2️⃣ `git log branchB..branchA` - Show commits on branchA not in branchB**
📌 **Exercise:**  
- Create two branches: `branchA` and `branchB`.
- Add different commits to each.
- Compare them using `git log`.

🛠 **Solution:**
```sh
git log branchB..branchA
```
This lists commits in `branchA` that are **not present** in `branchB`.

---

### **3️⃣ `git log --follow [file]` - Show commits that changed a file (even after renames)**
📌 **Exercise:**  
- Track the history of a renamed or modified file.
- Rename the file and commit the change.
- Use `git log --follow` to check its history.

🛠 **Solution:**
```sh
git log --follow myfile.txt
```
This displays commit history, even across renames.

---

### **4️⃣ `git diff branchB...branchA` - Show differences of what’s in branchA but not in branchB**
📌 **Exercise:**  
- Modify some files in `branchA`.
- Check the differences with `branchB`.

🛠 **Solution:**
```sh
git diff branchB...branchA
```
This shows **differences** between `branchA` and `branchB`.

---

### **5️⃣ `git show [SHA]` - Show any object in Git in a human-readable format**
📌 **Exercise:**  
- Identify a commit SHA using `git log`.
- Use `git show` to inspect the commit details.

🛠 **Solution:**
```sh
git show a1b2c3d4  # Replace with actual commit SHA
```
This provides detailed info about a specific commit.

---

### **6️⃣ `git remote add [alias] [url]` - Add a Git URL as an alias**
📌 **Exercise:**  
- Add a remote repository as an alias.

🛠 **Solution:**
```sh
git remote add origin https://github.com/user/repo.git
```
Now, `origin` is the alias for the GitHub repo.

---

### **7️⃣ `git fetch [alias]` - Fetch all branches from a remote**
📌 **Exercise:**  
- Fetch changes from the remote repository.

🛠 **Solution:**
```sh
git fetch origin
```
This retrieves the latest commits and branches from `origin`.

---

### **8️⃣ `git merge [alias]/[branch]` - Merge a remote branch into your local branch**
📌 **Exercise:**  
- Merge a remote branch into the current branch.

🛠 **Solution:**
```sh
git merge origin/main
```
This brings the latest changes from the `main` branch into your local branch.

---

### **9️⃣ `git push [alias] [branch]` - Push local commits to remote repository**
📌 **Exercise:**  
- Push local changes to GitHub.

🛠 **Solution:**
```sh
git push origin main
```
This updates the `main` branch on GitHub.

---

### **🔟 `git pull` - Fetch and merge commits from the tracking remote branch**
📌 **Exercise:**  
- Pull the latest changes from the remote repository.

🛠 **Solution:**
```sh
git pull origin main
```
This fetches and merges changes from `main`.

---

### **1️⃣1️⃣ `git rm [file]` - Delete a file and stage the removal**
📌 **Exercise:**  
- Delete a file and commit the removal.

🛠 **Solution:**
```sh
git rm unwanted-file.txt
git commit -m "Removed unwanted file"
```
This removes the file from the repo.

---

### **1️⃣2️⃣ `git mv [existing-path] [new-path]` - Rename a file and stage the move**
📌 **Exercise:**  
- Rename a file and commit the change.

🛠 **Solution:**
```sh
git mv oldfile.txt newfile.txt
git commit -m "Renamed file"
```
This ensures Git tracks the rename properly.

---

### **1️⃣3️⃣ `git log --stat -M` - Show commit logs with file moves**
📌 **Exercise:**  
- View commit logs with moved files.

🛠 **Solution:**
```sh
git log --stat -M
```
This shows file moves in commit history.

---

### **1️⃣4️⃣ `git rebase [branch]` - Apply commits of the current branch ahead of another**
📌 **Exercise:**  
- Rebase `feature-branch` onto `main`.

🛠 **Solution:**
```sh
git checkout feature-branch
git rebase main
```
This reapplies commits on top of `main`.

---

### **1️⃣5️⃣ `git reset --hard [commit]` - Reset working tree to a specific commit**
📌 **Exercise:**  
- Reset to a previous commit.

🛠 **Solution:**
```sh
git reset --hard a1b2c3d4
```
⚠️ This erases changes after the specified commit.

---

### **1️⃣6️⃣ `git stash` - Save modified and staged changes**
📌 **Exercise:**  
- Stash uncommitted changes.

🛠 **Solution:**
```sh
git stash
```
This saves changes without committing.

---

### **1️⃣7️⃣ `git stash list` - View stashed changes**
📌 **Exercise:**  
- List saved stashes.

🛠 **Solution:**
```sh
git stash list
```
This shows all stashed changes.

---

### **1️⃣8️⃣ `git stash pop` - Restore the top stash**
📌 **Exercise:**  
- Apply the latest stash.

🛠 **Solution:**
```sh
git stash pop
```
This restores the last saved state.

---

### **1️⃣9️⃣ `git stash drop` - Remove the top stash**
📌 **Exercise:**  
- Delete the most recent stash.

🛠 **Solution:**
```sh
git stash drop
```
This removes the last stash.

---

### **2️⃣0️⃣ `.gitignore` - Ignore specific files**
📌 **Exercise:**  
- Create a `.gitignore` file.

🛠 **Solution:**
```sh
echo "logs/" >> .gitignore
echo "*.notes" >> .gitignore
echo "pattern*/" >> .gitignore
```
This prevents Git from tracking ignored files.

---

### **2️⃣1️⃣ `git config --global core.excludesfile [file]` - Set a system-wide ignore file**
📌 **Exercise:**  
- Configure a global ignore file.

🛠 **Solution:**
```sh
git config --global core.excludesfile ~/.gitignore_global
```
This sets `.gitignore_global` as the default ignore file.

---

## **🔥 Summary of Key Learning Outcomes**
✅ Commit history tracking (`git log`, `git show`)  
✅ Branch comparison & merging (`git diff`, `git merge`)  
✅ Remote operations (`git push`, `git pull`, `git fetch`)  
✅ Stashing workflow (`git stash`, `git stash pop`)  
✅ Ignoring files (`.gitignore`, `git config --global core.excludesfile`)  
✅ Undoing changes (`git reset --hard`, `git rebase`)  

