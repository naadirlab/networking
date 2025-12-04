# Networking Assignment

## Deploying Nginx on an EC2 Instance and Connecting it to Cloudflare 
This project demonstrates how to deploy an NGINX web server on an AWS EC2 instance and connect it to a custom domain using Cloudflare DNS over **HTTP**.


## Step 1: Purchase a Domain on Cloudflare    

1. Navigate to Cloudflare and register a domain

2. Complete the Checkout 

![alt text](<Screenshots/Cloudflare Account Home.png>)

## Step 2: Launch an EC2 Instance on AWS

1. EC2 -> Instances -> Launch Instance  

2. Choose Amazon Linux as the machine image (AMI)

![alt text](<Screenshots/Launch Instance AWS.png>)

3. Create a new key pair (RSA,.pem)

![alt text](<Screenshots/Create Key Pair.png>)

4. Security Group configurations:
    - allow SSH traffic from My IP
    - allow HTTP traffic from anywhere anywhere (0.0.0.0/0)

![Screenshots/Security Group.png](<Screenshots/Security Group.png>)

5. Launch Instance

## Step 3: SSH into the EC2 Instance 

1. Select Instance and press "Connect" 

2. Open Terminal and navigate to the Downloads folder and confirm the private key is present

3. Secure the Private Key: 

```bash
chmod 400 my-ec2-key.pem
```

4. Connect through SSH  

![alt text](<Screenshots/Instance Connect.png>)
![alt text](<Screenshots/SSH Instance.png>)

## Step 4: Install and run NGINX 

1. Install and enable NGINX 

```bash
sudo yum install -y nginx
sudo systemctl enable nginx
```

2. Start NGINX 

```bash
sudo systemctl start nginx
```

## Step 5: Configure DNS 

1. Cloudflare -> DNS -> Records

2. Choose Type A (maps a domain name to an IPv4 address)

3. Enter the public IPv4 address of the EC2 instance and save the record

![alt text](<Screenshots/DNS Settings.png>)

## Final Result

A fully deployed Nginx server running on an EC2 instance, connected to your own Cloudflare domain. 

![alt text](<Screenshots/NGINX Landing Page.png>)
