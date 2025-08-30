## 🚀 GitHub SSH Setup Guide

##### This guide explains how to set up **SSH authentication** for GitHub so you can push and pull code without entering your username and password every time.
---
### 🔍 1. Check for Existing SSH Keys
Run:
```bash
ls -al ~/.ssh
```
If you see files like id_rsa.pub or id_ed25519.pub, you already have a key. Otherwise, generate one.

### 🔑 2. Generate a New SSH Key

##### Use your GitHub email:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
##### If ed25519 is not supported:
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
##### Press Enter to accept defaults. Add a passphrase if you want extra security.

### ⚡ 3. Start the SSH Agent
```bash
eval "$(ssh-agent -s)"

ssh-add ~/.ssh/id_ed25519
```

### 📝 4. Add SSH Key to GitHub

##### Copy your public key:
```bash
cat ~/.ssh/id_ed25519.pub
```
##### Then:
- Go to 👉 GitHub → Settings → SSH and GPG keys
- Click New SSH Key
- Paste the key and save

### ✅ 5. Test the Connection
```bash
ssh -T git@github.com
```
##### You should see:
```bash
Hi <username>! You've successfully authenticated, but GitHub does not provide shell access.
```
### 6. Update Git Remote to Use SSH

### Switch your remote to SSH:

##### 🎉 You’re all set! You can now git clone, git push, and git pull securely using SSH.
---
