

# E-Commerce MVP Deployment on AWS

🚀 **Build an E-Commerce MVP on AWS in Under 2 Hours**  
Real-World DevOps Project Using **Terraform**, **Ansible**, & **Magento**

![PORTFOLIO PROJECTS_AWS - MODULE 7_THUMBNAIL](https://github.com/user-attachments/assets/6721bdbf-aece-436d-94d4-f6ca185440eb)




---

## 🛠️ Role: Cloud Engineer | DevOps Implementation | Real-World Scenario

### 🧩 Problem Statement
Many startups or small businesses need to launch e-commerce platforms quickly to validate their idea or reach the market early — but without sacrificing scalability, maintainability, and automation.  
Manual deployment is time-consuming, error-prone, and not repeatable.  

**Challenge:**  
How can we deploy a fully functional Magento-based e-commerce platform on AWS in under 2 hours, using Infrastructure as Code (IaC)?

---

## ✅ Solution Overview

This project demonstrates how to deploy a Minimum Viable Product (MVP) of an e-commerce website in an automated, scalable, and production-ready way using:

- **Terraform** for infrastructure provisioning  
- **Ansible** for configuration management and software installation  
- **Magento** (open-source e-commerce platform)  
- **PHP**, **MySQL**, and **Redis** for the backend stack  
- **AWS EC2** for compute resources  

By leveraging **Infrastructure as Code (IaC)**, the solution is fast to deploy, reusable, scalable, and easy to maintain.

![PORTFOLIO PROJECTS_AWS - MODULE 7_ARCHITECTURE](https://github.com/user-attachments/assets/d8556358-79e3-4a03-82b6-88ba64758c68)



---

## 🏗️ Step-by-Step Implementation

### Part 1: Infrastructure Provisioning with Terraform

1. **Environment Setup**  
   - Launched the project on AWS CloudShell  
   - Installed Terraform using Amazon Linux commands  

2. **Project Initialization**  
   ```bash
   mkdir ecommerce-mvp && cd ecommerce-mvp
   git clone https://github.com/abdihakim-said/e-commerce-MVP-deployment
   cd terraform
   ```

3. **Configure Terraform Variables**  
   Updated `main.tf` to use:  
   - Default VPC  
   - Key pair: `ssh-aws-bootcamp`  
   - EC2 instance type: `t3a.large`  

4. **Run Terraform Commands**  
   ```bash
   terraform init
   terraform plan
   terraform apply
   ```
   This spun up an EC2 instance with the desired specifications, recording infrastructure state in `terraform.tfstate`.

---

### Part 2: Server Configuration with Ansible

1. **Connect to EC2 Instance**  
   ```bash
   ssh -i ssh-aws-bootcamp.pem ec2-user@<EC2_PUBLIC_IP>
   ```

2. **Install Ansible**  
   ```bash
   sudo yum-config-manager --enable epel
   sudo yum install ansible -y
   ```

3. **Download and Configure Ansible Playbooks**  
   ```bash
   git clone https://github.com/abdihakim-said/e-commerce-MVP-deployment
   cd ansible-magento
   vi group_vars/all.yml
   ```
   Updated `group_vars/all.yml` with:  
   - Magento public/private keys  
   - EC2 public IP as domain and hostname  

4. **Run the Ansible Playbook**  
   ```bash
   ansible-playbook -i hosts.yml ansible-magento2.yml -k -vvv --become
   ```
   This handled:  
   - LAMP/LEMP stack installation  
   - Magento installation  
   - PHP, MySQL, Redis configuration  
   - File permissions, user creation, services  

---

## 🌐 Outcome

✅ Successfully deployed a fully working e-commerce MVP using Magento in less than 2 hours.  
✅ Automated both infrastructure and software deployment — no manual steps beyond IP configuration and Ansible variable changes.  
✅ Demonstrated how DevOps practices (IaC, configuration management, automation) can deliver fast, reliable deployments — ideal for startups and lean teams.  

<img width="1440" alt="Screenshot 2025-05-03 at 06 07 36" src="https://github.com/user-attachments/assets/c68ca564-b991-4285-ab0f-a3cbe62b995a" />



---

## 📉 Challenges Faced

- **Magento Dependency Management:** Required Magento marketplace access keys (API keys) for package installation, which had to be securely managed in Ansible.  
- **PHP Version Compatibility:** Magento is sensitive to PHP versions. Ensuring the correct version was installed required extra attention.  
- **Redis Integration:** Tuning Redis for Magento's full-page caching required playbook adjustments.  
- **Public IP Changes:** EC2 public IP changes on every restart; unless using Elastic IP, manual updates are needed in Ansible variables.  
- **Cache Issues:** Magento's aggressive caching required manual flushing to reflect UI changes.  

---

## 💡 Lessons Learned

- Speed and repeatability are crucial in MVP scenarios — Terraform and Ansible are powerful allies.  
- Using IaC from day one saves time and avoids configuration drift.  
- Testing locally or in staging helps iron out environmental and dependency issues.  
- Documentation and modularization of Ansible roles make the stack more maintainable.  

---

## 📸 Final Look

After deploying, visit:  
- **Storefront:** `http://<EC2_PUBLIC_IP>`  
- **Admin Dashboard:** `http://<EC2_PUBLIC_IP>/securelocation`  
  - **User:** Admin  
  - **Password:** Strong123Password#  

<img width="1440" alt="Screenshot 2025-05-03 at 06 08 03" src="https://github.com/user-attachments/assets/fcbdcc10-3b4b-438b-86a2-85ad2758ead4" />


<img width="1440" alt="Screenshot 2025-05-03 at 06 08 15" src="https://github.com/user-attachments/assets/2079a304-b1ef-4da9-8805-8bcc2c44c60a" />

<img width="1440" alt="Screenshot 2025-05-03 at 06 08 30" src="https://github.com/user-attachments/assets/d608b510-4cb7-4df9-86a1-115bae8c16eb" />

---

## 🧹 Clean-up

Once testing is done, destroy all resources:  
```bash
cd terraform
terraform destroy
```

---

## 📚 References

- [Magento Marketplace](https://marketplace.magento.com/)  
- [Ansible Documentation](https://docs.ansible.com/)  
- [AWS EC2 Pricing](https://aws.amazon.com/ec2/pricing/)  
- [Terraform Registry](https://registry.terraform.io/)  

---

## 🔗 GitHub Repository

All code used in this project, including Terraform and Ansible files, is available publicly:  
[E-Commerce MVP Deployment](https://github.com/abdihakim-said/e-commerce-MVP-deployment)  

--- 

✨ **Final Thoughts**  
This real-world scenario demonstrates the power of DevOps and Cloud Engineering to deliver fast, scalable, and production-ready solutions with minimal human effort.  
This project proves that even complex platforms like Magento can be fully automated using the right tools and mindset.
