# GitHub Setup Guide for Windows (Git Bash)

This guide provides a structured walkthrough to set up GitHub on your PC using Git Bash.

---
## 📑 Table of Contents
<!-- TOC -->

- [GitHub Setup Guide for Windows (Git Bash)](#github-setup-guide-for-windows-git-bash)
  - [📑 Table of Contents](#-table-of-contents)
  - [📋 Prerequisites](#-prerequisites)
  - [📄 0. Bash Profile Configuration](#-0-bash-profile-configuration)
  - [🚀 1. Configuring Git](#-1-configuring-git)
    - [Check Git Version](#check-git-version)
    - [Set Global Git Configuration](#set-global-git-configuration)
  - [🔐 2. Setting Up SSH for GitHub](#-2-setting-up-ssh-for-github)
    - [Generate SSH Key](#generate-ssh-key)
    - [Start SSH Agent](#start-ssh-agent)
    - [Add SSH Key to Agent](#add-ssh-key-to-agent)
    - [Add SSH Key to GitHub](#add-ssh-key-to-github)
    - [Test SSH Connection](#test-ssh-connection)
  - [📦 3. Repository Setup](#-3-repository-setup)
    - [Initialize a New Git Repository](#initialize-a-new-git-repository)
    - [Add and Commit Files](#add-and-commit-files)
    - [Add Remote Repository](#add-remote-repository)
    - [Push to GitHub](#push-to-github)
    - [Push an existing repository from the command line](#push-an-existing-repository-from-the-command-line)
  - [🔄 4. Pull Existing Repository](#-4-pull-existing-repository)
    - [Pull existing repository to local](#pull-existing-repository-to-local)
  - [🗂️ 5. Branching and Merging](#️-5-branching-and-merging)
    - [Create and Switch to a New Branch](#create-and-switch-to-a-new-branch)
    - [Push the Branch to GitHub](#push-the-branch-to-github)
    - [Merge Changes into Main Branch](#merge-changes-into-main-branch)
    - [Move repo directory to new directory](#move-repo-directory-to-new-directory)
    - [Remove and Reconnect to remote repository](#remove-and-reconnect-to-remote-repository)
    - [Delete branch \& remote branch](#delete-branch--remote-branch)
    - [Verify branch](#verify-branch)
    - [Safely Delete .git directory](#safely-delete-git-directory)
  - [⚙️ 6. Using GitHub CLI (Optional)](#️-6-using-github-cli-optional)
    - [Verify GitHub CLI Installation](#verify-github-cli-installation)
    - [Authenticate with GitHub](#authenticate-with-github)
    - [Create Repository Using GitHub CLI](#create-repository-using-github-cli)
    - [Open Repository in Browser](#open-repository-in-browser)
  - [📦 7. Release code \& tagging](#-7-release-code--tagging)
  - [📝 8. Troubleshooting Common Issues](#-8-troubleshooting-common-issues)
  - [💡 9. Helpful Commands](#-9-helpful-commands)
  - [✅ Conclusion](#-conclusion)

<!-- /TOC -->


---

## 📋 Prerequisites

- **Git** installed: [Download Git](https://git-scm.com/downloads)
- **GitHub account** created: [Sign up](https://github.com/join)
- **GitHub CLI** (optional for advanced features): [Download GitHub CLI](https://cli.github.com/)

---

## 📄 0. Bash Profile Configuration

```bash
cat ~/.bash_profile
```
```properties
export MY_PATH="/c/Users/mifta/OneDrive - IBM/IBM/LEARNING"
alias mydir='cd "$MY_PATH"'
export PATH=$PATH:/c/Program\ Files/GitHub\ CLI
```
```bash
source ~/.bash_profile
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

For organization login:
```bash
git config --global user.name "Miftah-Choiri"
git config --global user.email "miftah.choiri@ibm.com"
git config -list
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

For Organization ssh-connection:
```bash
ssh-keygen -t ed25519 -C "miftah.choiri@ibm.com"
```
```bash
# save the key into different location
Enter file in which to save the key (/c/Users/mifta/.ssh/id_ed25519): /c/Users/mifta/.ssh/id_ed25519_ibm
```
```bash
ll ~/.ssh/
vi ~/.ssh/config
```
```properties
# Personal GitHub Account
Host github.com-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_ed25519

# IBM GitHub Account
Host github.com-ibm
    HostName github.ibm.com
    User git
    IdentityFile ~/.ssh/id_ed25519_ibm
```
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519_ibm
```
```bash
Identity added: /c/Users/mifta/.ssh/id_ed25519_ibm (miftah.choiri@ibm.com)
```
Test connection to github.com & github.ibm.com
```bash
ssh -i ~/.ssh/id_ed25519_ibm -T git@github.ibm.com
```
```bash
Hi Miftah-Choiri! You've successfully authenticated, but GitHub does not provide shell access.
```
```bash
ssh -T git@github.com
```
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
git branch -M main
git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
```
```bash
gh auth login
gh repo create how-to-setup-github --public --source=. --remote=origin --push
```

### Push to GitHub

```bash
git push -u origin main
```
### Push an existing repository from the command line
```bash
git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
git branch -M main
git push -u origin main
```
---

## 🔄 4. Pull Existing Repository

### Pull existing repository to local

```bash
git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
git pull origin main
# or
git pull git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
```
```bash
git remote -v
git remote set-url origin git@github.com:miftah-ahmad-choiri/miftah-ahmad-choiri.github.io.git
git pull origin master
```

---

## 🗂️ 5. Branching and Merging

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

### Move repo directory to new directory
```bash
cp -r how-to-setup-github/ repository/
rm -rf how-to-setup-github/
```

### Remove and Reconnect to remote repository
```bash
git remote remove origin
git remote -r

git remote add origin git@github.com:miftah-ahmad-choiri/how-to-setup-github.git
git remote -r
```

### Delete branch & remote branch
```bash
git branch -d edit-readme
git branch -D edit-readme
git push origin --delete edit-readme
```

### Verify branch
```bash
git branch
git branch -r
```
### Safely Delete .git directory
```bash
# remove .git file from repo directory
cd how-to-setup-github
rm -rf .git
cd ..
rm -rf how-to-setup-github
```

---

## ⚙️ 6. Using GitHub CLI (Optional)

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

## 📦 7. Release code & tagging

**Create a Release Tag**
```bash
git tag -a v0.1.0 -m "Release version 0.1.0"
git push origin v0.1.0
```
**Zip file except .git**
```bash
cd how-to-setup-github
sudo zip -r ../public/releases/how-to-setup-github.zip . -x ".git/*"
```
**How to unzip**
```bash
cd ../public/releases/how-to-setup-github.zip
unzip how-to-setup-github.zip -d how-to-setup-github
```
**Upload .zip file to release repo**
```bash
git status
git add .
git commit -m 'ready to publish release v.0.1.0'
git push -u origin main
gh auth login
# make sure you commit and push your latest code before publish release
gh release create v0.1.0 --title "Release v0.1.0" --notes "Initial release notes."
# or upload it manually to release version v0.1.0
gh release upload v0.1.0 ../public/releases/how-to-setup-github.zip
```
**Remove a release from github repo**
```bash
gh release list
gh release delete v0.1.0
```
---

## 📝 8. Troubleshooting Common Issues

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

## 💡 9. Helpful Commands

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

