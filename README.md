# 🚀 Deploying a Node.js Application on AWS EC2

This guide walks you through setting up, testing, and deploying a Node.js project on an AWS EC2 instance running Ubuntu.

---

## 📦 Project Setup (Local Machine)

### 1. Clone the Repository
```bash
git clone https://github.com/arun-4321/AWS-Session.git
cd AWS-Session
```

### 2. Configure Environment Variables  
Create a `.env` file in the root of the project and add:
```env
DOMAIN=""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```

### 3. Install Dependencies & Start Server
```bash
npm install
npm run start
```
Visit `http://localhost:3000` to verify it’s running locally.

---

## ☁️ AWS EC2 Deployment

### 1. AWS Account Setup
- Log in to the [AWS Console](https://console.aws.amazon.com/)
- Create an **IAM user**  
  - Access type: **Password**  
  - Permissions: **Admin**

### 2. Launch an EC2 Instance
- **OS**: Ubuntu  
- **Instance type**: `t2.micro` (Free Tier Eligible)  
- Create and download a new key pair (`.pem` file)  
- Launch instance  

---

## 🔐 Connect to EC2 via SSH
```bash
chmod 400 instance.pem
ssh -i instance.pem ubuntu@<YOUR_PUBLIC_IP>
```

---

## 🛠️ Configure Ubuntu VM

### 1. Update Packages
```bash
sudo apt update
```

### 2. Install Git
```bash
sudo apt install git -y
```

### 3. Install Node.js & npm
```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```
Verify versions:
```bash
node -v
npm -v
```

---

## 🚀 Deploy Project on EC2

### 1. Clone the Project
```bash
git clone https://github.com/arun-4321/AWS-Session.git
cd AWS-Session
```

### 2. Set Up Environment Variables  
Create a `.env` file:
```env
DOMAIN="<YOUR_ELASTIC_IP>"
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY=""
SECRET_KEY=""
```

### 3. Install & Start Project
```bash
npm install
npm run start
```

---

## 🌐 Configure Security Group

1. Go to **EC2 Dashboard → Security Groups**  
2. Edit **Inbound Rules**  
3. Add:
```
Type: Custom TCP
Port: 3000
Source: 0.0.0.0/0   # or restrict to your IP
```
Now visit **http://<YOUR_ELASTIC_IP>:3000**

---



## ✅ Done!

Your Node.js application is now live on AWS EC2 🎉  
Visit: **http://<YOUR_ELASTIC_IP>:3000**

---

## 📎 Resources
- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)  
- [Node.js on Ubuntu](https://github.com/nodesource/distributions)  
- [PM2 Process Manager](https://pm2.keymetrics.io/)  

**Happy Shipping! 🚀**
