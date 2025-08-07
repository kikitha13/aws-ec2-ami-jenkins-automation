#  AWS EC2 AMI & Launch Template for Automated Jenkins Deployment

> **Author:** Ravilla Kikitha  
> **Use Case:** DevOps | AWS Infrastructure | Jenkins Automation | AMI & Launch Template  
> **Level:** Beginner to Intermediate  

---

##  Description

This project demonstrates how to create a scalable and reusable infrastructure setup on AWS by building a custom AMI (Amazon Machine Image) from an EC2 instance and using it in a Launch Template. Jenkins, a powerful automation server for CI/CD, is installed and configured on the instance to create a pre-baked infrastructure that reduces repetitive setup and accelerates development workflows.

---

##  Why This Project?

In the real world, DevOps engineers often need to create **repeatable infrastructure** that can be quickly replicated and launched. Instead of setting up Jenkins on every new EC2 manually, this project helps you:

- Automate Jenkins installation.
- Save time using pre-configured AMIs.
- Build scalable launch templates.
- Improve consistency across environments.

This project is perfect for:
- Final-year students
- AWS beginners
- Job seekers building DevOps portfolios

---

##  AWS Services Used

| AWS Service        | Purpose                                                                 |
|--------------------|-------------------------------------------------------------------------|
| **EC2**            | Host Linux-based virtual machines                                       |
| **AMI**            | Store a configured image of an EC2 instance                             |
| **Launch Template**| Define a template to launch multiple instances easily                   |
| **Security Groups**| Control access (e.g., SSH 22, Jenkins 8080)                             |
| **Key Pairs**      | For secure remote access to the instance                                |
| **User Data**      | Automate installation at instance boot                                  |

---

##  Project Workflow

###  Step 1: Create Base EC2 Instance (`ec2-1`)

- Launch an EC2 instance with:
  - **ubuntu**
  - **Instance Type:** t2.micro (Free Tier)
  - **Key Pair:** `my-key.pem`
  - **Security Group:**
    - SSH – Port 22 (Your IP)
    - HTTP – Port 8080 (for Jenkins, Your IP)

 
 ![WhatsApp Image 2025-08-06 at 16 02 53_3b78bb08](https://github.com/user-attachments/assets/f20813d8-21bc-47b8-8323-1013f0174396)


---

### 🔗 Step 2: Connect to EC2

#### Option 1: Using EC2 Instance Connect  
Use the AWS Console to connect directly.

#### Option 2: if you Using Git Bash  
```bash
ssh -i "my-key.pem" ec2-user@<public-ip-address>


---


### Step 3: Install Jenkins on EC2
Run these commands inside your EC2 terminal:
# 1. Update system packages
sudo apt update -y
sudo apt upgrade -y

# 2. Install Java (required for Jenkins)
sudo apt install openjdk-11-jdk -y

# 3. Add Jenkins repository key
curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# 4. Add Jenkins repository
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

# 5. Update package list
sudo apt update -y

# 6. Install Jenkins
sudo apt install jenkins -y

# 7. Start Jenkins
sudo systemctl start jenkins

# 8. Enable Jenkins to start on boot
sudo systemctl enable jenkins

🔐 Step 4: Access Jenkins Web UI
Open your browser:
http://<public-ip>:8080
To get the admin password:
bash command:
sudo cat /var/lib/jenkins/secrets/initialAdminPassword



