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
  - **Amazon Linux 2**
  - **Instance Type:** t2.micro (Free Tier)
  - **Key Pair:** `my-key.pem`
  - **Security Group:**
    - SSH – Port 22 (Your IP)
    - HTTP – Port 8080 (for Jenkins, Your IP)

 *Screenshot: EC2 Launch Settings*

---

### 🔗 Step 2: Connect to EC2

#### Option 1: Using EC2 Instance Connect  
Use the AWS Console to connect directly.

#### Option 2: Using Git Bash  
```bash
ssh -i "my-key.pem" ec2-user@<public-ip-address>

