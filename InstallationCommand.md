
# Jenkins and Docker Full Setup Guide

This document provides a step-by-step shell command reference for setting up Jenkins, Docker, Trivy, and deploying a sample containerized application.

---

## 📦 System Update and Java Installation

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install openjdk-11-jdk
```

---

## 🛠️ Add Jenkins Repository and Install Jenkins

```bash
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

# (Optional duplicate steps - can skip if already added)
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA
sudo apt install jenkins
```

---

## ☕ Install Java 17 and Validate

```bash
sudo apt update
sudo apt install fontconfig openjdk-17-jre
java --version
```

---

## 🔐 Secure Jenkins Repo and Install Again (Preferred Method)

```bash
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian binary/" | \
sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt-get update
sudo apt-get install jenkins
```

---

## ✅ Check Jenkins Status

```bash
sudo systemctl status jenkins
```

---

## 🔑 Get Jenkins Initial Admin Password

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

## 🐳 Docker Installation

```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
sudo mkdir -p /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker --version
```

---

## 👤 Add Jenkins to Docker Group

```bash
sudo usermod -aG docker jenkins
sudo systemctl restart jenkins
```

---

## 🔍 Trivy Installation (Vulnerability Scanner)

```bash
sudo apt-get install wget apt-transport-https gnupg lsb-release

wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | \
sudo tee -a /etc/apt/sources.list.d/trivy.list

sudo apt-get update
sudo apt-get install trivy
```

---

## 🧹 Docker Cleanup Commands

```bash
df -h

# Remove stopped containers
docker container prune -f

# Remove unused images
docker image prune -a -f

# Remove unused volumes
docker volume prune -f

# Remove unused networks
docker network prune -f
```

---

## 🐳 Docker Usage

```bash
lsblk
df -h
docker login
docker login -u devski
docker ps
docker ps -a
docker run -d -p 8000:8000 --name test-notes-container devski/my-notes-app:latest
```

---

## 🧱 Docker Compose Manual Installation

```bash
sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" \
-o /usr/local/bin/docker-compose

sudo chmod +x /usr/local/bin/docker-compose
docker-compose
docker-compose ps
docker compose ps
```

---

## 🔐 Retrieve Jenkins Password Again

```bash
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

---

## 🧪 Test Your App

```bash
curl http://localhost:8000
```

---

## 🧾 Miscellaneous Commands

```bash
history
sudo su
ls
```

---
