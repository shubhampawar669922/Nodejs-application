# Deploying a node.js application on AWS Ec2 instance

## Introduction

This project demonstrates how to host a Node.js application on an AWS EC2 instance.

Note: When deploying a Node.js application, you don’t need an additional web server—Node.js itself can act as the web server.

The steps are written in a simple way so that anyone can follow them easily. All you need is an EC2 instance, Node.js as the web server, and npm as the package manager.

## Requirements

1. AWS account with an EC2 instance (Linux-based)

2. SSH key pair to connect to the instance

3. Node.js and npm installed on EC2

4. Security group with HTTP (port 80) or app port open

5. Your Node.js application code.

## Deployment Steps:

### Step 1: Launch an EC2 Instance

Go to AWS Management Console --> EC2 --> Launch instance  (named as NodeApp)

Choose Amazon Linux AMI

Select instance type(t3.micro for free tier)

Configure security group --> Allow HTTP(80),HTTPS(443),SSH(22)

Click Launch Instance = Wait until the status shows running.

Creating and instance.

![node1](./images/node1.png)

![node2](./images/node2.png)

![node3](./images/node3.png)


### Step 2: Connecting to EC2 instance

Run this command on terminal-

ssh -i "your-key-pem" ec2-user@your-public-ip

![node4](./images/node4.png)


### Step 3: Updating Packages

Run this command on terminal-

sudo yum update

![node5](./images/node5.png)

### Step 4: Installing Node.js as a webserver and NPM as a package manager

sudo yum install nodejs -y

sudo yum install npm -y

![node6](./images/node6.png)

![node7](./images/node7.png)

### Step 5: Check Versions
node --version

npm --version

![node8](./images/node8.png)

![node9](./images/node9.png)

### Step 6: Create Directory

mkdir nodeapp

![node10](./images/node10.png)

### Step 7: Verify Directory

ls



### Step 8: Go Inside Directory

cd nodeapp/

ls

![node11](./images/node11.png)

### Step 9: Check Git Installation

git --version


If not installed:

sudo yum install git

![node12](./images/node12.png)

### Step 10: Check Git Version

git --version

![node13](./images/node13.png)


### Step 11: Clone Your Application Code

sudo git clone " your-repository-link"

![node14](./images/node14.png)

### Step 12: Go to Cloned Project

ls

cd node-app/

![node15](./images/node15.png)

### Step 13: Verify Files

ls



### Step 14: Check for package.json and app.js


Ignore Dockerfile if present.

![node16](./images/node16.png)

### Step 15: View package.json


cat package.json

![node17](./images/node17.png)

### Step 16: Install Dependencies


sudo npm install

### Step 17: Check node_modules Folder

If present, all dependencies are installed successfully.

![node18](./images/node18.png)

### Step 18: View app.js File


cat app.js

![node19](./images/node19.png)

### Step 19: Run Application
node app.js


You should see:

Server is running...

![node20](./images/node20.png)

### Step 20: Configure Security Group

Go to AWS Security Group settings

Add a new inbound rule:

Type: Custom TCP

Port: 3000

Source: Anywhere (IPv4)

![node21](./images/node21.png)

### Step 21: Access Application

Copy your EC2 Public IP and open it in browser with port 3000:

http://"public-ip":3000

![node22](./images/node22.png)



### Step 22: Run Application in Background (Optional)

If you want your app to keep running after closing the terminal:

sudo npm install -g pm2

pm2 start app.js


Now refresh your browser — your app will still be running.

![node23](./images/node23.png)

![node24](./images/node24.png)

This is final output of your project.