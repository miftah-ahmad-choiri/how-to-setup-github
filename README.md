# GitHub Setup Guide for Windows (Git Bash)

This guide provides a structured walkthrough to set up GitHub on your PC using Git Bash.

---

## 📑 Table of Contents
1. [Bash Profile Configuration](#-8-bash-profile-configuration)
2. [Prerequisites](#-prerequisites)
3. [Configuring Git](#-1-configuring-git)
4. [Setting Up SSH for GitHub](#-2-setting-up-ssh-for-github)
5. [Repository Setup](#-3-repository-setup)
6. [Branching and Merging](#-4-branching-and-merging)
7. [Using GitHub CLI (Optional)](#-5-using-github-cli-optional)
8. [Troubleshooting Common Issues](#-6-troubleshooting-common-issues)
9. [Helpful Commands](#-7-helpful-commands)
10. [Conclusion](#-conclusion)

---

## 📋 Prerequisites

- **Git** installed: [Download Git](https://git-scm.com/downloads)
- **GitHub account** created: [Sign up](https://github.com/join)
- **GitHub CLI** (optional for advanced features): [Download GitHub CLI](https://cli.github.com/)

---

## 📄 0. Bash Profile Configuration

```bash
$ cat ~/.bash_profile
export MY_PATH="/c/Users/mifta/OneDrive - IBM/IBM/LEARNING"
alias mydir='cd "$MY_PATH"'
export PATH=$PATH:/c/Program\ Files/GitHub\ CLI

$ source ~/.bash_profile
```

This configuration sets a custom path environment and alias for easier navigation and ensures the GitHub CLI is accessible from Git Bash.


---

## 🚀 1. Configuring Git

### Check Git Version

```bash
git --version
```

Ensure Git is installed correctly.

### Set Global Git Configuration

```bash
git config --global user.name "miftah-ahmad-choiri"
git config --global user.email "miftahcoiri354@gmail.com"
```

Verify settings:

```bash
git config --list
```

---

## 🔐 2. Setting Up SSH for GitHub

### Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "miftahcoiri354@gmail.com"
```

Press Enter to accept defaults and optionally set a passphrase.

### Start SSH Agent

```bash
eval "$(ssh-agent -s)"
```

### Add SSH Key to Agent

```bash
ssh-add ~/.ssh/id_ed25519
```

### Add SSH Key to GitHub

1. Display the public key:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
2. Copy the key.
3. Go to **GitHub → Settings → SSH and GPG keys → New SSH key**.
4. Paste the key and save.

### Test SSH Connection

```bash
ssh -T git@github.com
```

Successful output:

```bash
Hi miftah-ahmad-choiri! You've successfully authenticated, but GitHub does not provide shell access.
```

---

## 📦 3. Repository Setup

### Initialize a New Git Repository

```bash
cd ~/OneDrive - IBM/IBM/LEARNING/github/how-to-setup-github/
git init
```

### Add and Commit Files

```bash
git add how-to-setup-github.md
git commit -m "Initial commit"
```

### Add Remote Repository

```bash
git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
```

### Push to GitHub

```bash
git push -u origin main
```

---

## 🗂️ 4. Branching and Merging

### Create and Switch to a New Branch

```bash
git checkout -b edit-readme
```

### Push the Branch to GitHub

```bash
git push -u origin edit-readme
```

### Merge Changes into Main Branch

```bash
git checkout main
git merge edit-readme
git push origin main
```

---

## ⚙️ 5. Using GitHub CLI (Optional)

### Verify GitHub CLI Installation

```bash
gh --version
```

### Authenticate with GitHub

```bash
gh auth login
```

Follow the prompts to authenticate via browser.

### Create Repository Using GitHub CLI

```bash
gh repo create how-to-setup-github --public --source=. --remote=origin --push
```

### Open Repository in Browser

```bash
gh repo view --web
```

---

## 📝 6. Troubleshooting Common Issues

- **Repository Not Found:**

  ```bash
  ERROR: Repository not found.
  ```

  **Fix:** Verify repository URL and access permissions.

- **Remote Already Exists:**

  ```bash
  error: remote origin already exists.
  ```

  **Fix:** Remove existing remote and add again:

  ```bash
  git remote remove origin
  git remote add origin git@github.com:USERNAME/REPO.git
  ```

---

## 💡 7. Helpful Commands

- List branches:
  ```bash
  git branch -a
  ```
- Check remote repositories:
  ```bash
  git remote -v
  ```
- View repository list:
  ```bash
  gh repo list
  ```


---

## ✅ Conclusion

This guide covers the end-to-end process of setting up GitHub on your PC, configuring Git, managing SSH keys, creating repositories, and working with branches. For more details, refer to [GitHub Docs](https://docs.github.com/).

---

**Author:** *Miftah Ahmad Choiri*  
**Last Updated:** *2025-02-01*

