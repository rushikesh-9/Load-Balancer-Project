# Load Balancer Project using Ansible

This project demonstrates how to automate the setup of a load balancer architecture using **Ansible**.  
It installs and configures **Apache web servers** and an **HAProxy load balancer** to distribute traffic across multiple backend servers.  

----------------------------------------------------------------

## 🚀 Features
- Automated installation of **Apache** on backend web servers.
- Configuration of **HAProxy** as the load balancer.
- Firewall rules to allow HTTP/HTTPS traffic.
- Simple and reusable Ansible playbook structure with roles.

---------------------------------------------------------------

## 📋 Prerequisites
- Ansible installed on the control machine.
- At least **2 backend servers** for Apache.
- **1 server** for HAProxy load balancer.
- SSH access to all servers.
- Python installed on target machines.

--------------------------------------------------------------
## ⚙️ Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/rushikesh-9/Load-Balancer-Project.git
   cd Load-Balancer-Project
2. Update the inventory file with your server details.
3. Run the playbook

      ansible-playbook -i inventory playbook.yml

------------------------------------------------------------
---
# Playbook for Load Balancer Project using Ansible

# Setup Web Servers
- name: Setup Apache Web Servers
  hosts: web_servers
  become: yes
  roles:
    - apache
    - firewall
# Setup Load Balancer
- name: Setup HAProxy Load Balancer
  hosts: balancer
  become: yes
  vars:
    web_backend:
      - name: web-server-1
        ip: 192.168.222.130
        port: 80
      - name: web-server-2
        ip: 192.168.222.131
        port: 80
    web_frontend:
      server: load-balancer
      port: 80
  roles:
    - haproxy
    - firewall
---------------------------------------------------------------------

👨‍💻 Author

Rushikesh Chandanwar
Ansible Automation Project for Load Balancer Setup 🚀
