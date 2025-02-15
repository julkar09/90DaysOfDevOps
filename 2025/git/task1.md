# Week 4: Git and GitHub Challenge Documentation

## Introduction
This documentation covers all the tasks performed for Week 4 of the **90 Days of DevOps - 2025 Edition** Git and GitHub Challenge. The tasks include forking, cloning, repository initialization, authentication, branching, pushing changes, and SSH authentication.

---

## Task 1: Fork and Clone the Repository

### Steps:
1. **Fork the Repository**  
   - Navigated to [90DaysOfDevOps](https://github.com/LondheShubham153/90DaysOfDevOps) and forked the repository.

2. **Clone the Repository**
   ```bash
   git clone https://github.com/julkar09/90DaysOfDevOps.git
   cd 90DaysOfDevOps/2025/git/01_Git_and_Github_Basics
   ```

---

## Task 2: Initialize a Local Repository and Create a File

### Steps:
1. **Create a Directory for the Challenge**
   ```bash
   mkdir week-4-challenge
   cd week-4-challenge
   ```

2. **Initialize a Git Repository**
   ```bash
   git init
   ```

3. **Create a File**
   ```bash
   echo "Julkar | DevOps Engineer in Training" > info.txt
   ```

4. **Stage and Commit the File**
   ```bash
   git add info.txt
   git commit -m "Initial commit: Add info.txt with introductory content"
   ```

---

## Task 3: Configure Remote URL with PAT and Push/Pull

### Steps:
1. **Set Up Remote Repository Using PAT**
   ```bash
   git remote add origin https://julkar09:<your-PAT>@github.com/julkar09/90DaysOfDevOps.git
   ```

2. **Push the Changes to Remote Repository**
   ```bash
   git push -u origin main
   ```

3. **Pull Remote Changes** (if needed)
   ```bash
   git pull origin main
   ```

---

## Task 4: Explore Commit History

### Steps:
1. **View Commit History**
   ```bash
   git log --oneline --graph --decorate
   ```

---

## Task 5: Advanced Branching and Switching

### Steps:
1. **Create a New Branch**
   ```bash
   git branch feature-update
   ```

2. **Switch to the New Branch**
   ```bash
   git switch feature-update
   ```

3. **Modify info.txt and Commit Changes**
   ```bash
   echo "Adding more details to info.txt" >> info.txt
   git add info.txt
   git commit -m "Feature update: Enhance info.txt with additional details"
   git push origin feature-update
   ```

4. **Merge Branch via Pull Request on GitHub**

---

## Task 6: Explain Branching Strategies

### Importance of Branching Strategies:
1. **Isolating Features and Bug Fixes**  
   - Developers can work independently on features and fixes without disrupting the main branch.

2. **Facilitating Parallel Development**  
   - Teams can work on different features simultaneously, improving efficiency.

3. **Reducing Merge Conflicts**  
   - Keeping feature branches isolated prevents unnecessary conflicts when merging changes.

4. **Enabling Effective Code Reviews**  
   - Pull Requests allow peer reviews before merging to ensure quality.

---

## Bonus Task: SSH Authentication

### Steps:
1. **Generate an SSH Key**
   ```bash
   ssh-keygen -t ed25519 -C "your-email@example.com"
   ```

2. **Add SSH Key to GitHub**
   - Copied the public key (`~/.ssh/id_ed25519.pub`) and added it to GitHub under **SSH and GPG keys**.

3. **Switch Remote to SSH**
   ```bash
   git remote set-url origin git@github.com:julkar09/90DaysOfDevOps.git
   ```

4. **Push Changes Using SSH**
   ```bash
   git push origin feature-update
   ```

---

