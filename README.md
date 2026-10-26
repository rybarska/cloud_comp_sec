Multi-Cloud Secure CI/CD Infrastructure (AWS & OCI)

> **Course Context:** Developed as a practical lab exercise for the **Cloud Computing Security** course at **St. Pölten University of Applied Sciences (FH St. Pölten)**.

This repository automates the deployment and security orchestration of a 
multi-cloud lab environment linking Amazon Web Services (AWS) and Oracle Cloud 
Infrastructure (OCI) via a site-to-site IPsec VPN, managed entirely through GitHub 
Actions and Ansible.

Architecture & Key Features
Multi-Cloud Site-to-Site VPN: Automatically configures and initiates an encrypted 
strongSwan IPsec tunnel bridging OCI (138.2.139.105) and AWS (34.234.148.108) 
network gateways.

Automated CI/CD Pipeline: Orchestrated via GitHub Actions, handling environment 
bootstrapping, key sanitization, and playbook execution on every push to main.

Zero-Trust Secret Management: Leverages GitHub Repository Secrets and Ansible 
Vault, safely passing credentials via ephemeral files and runtime systemd 
environment injection (DB_PASSWORD) to keep source code secure.

Isolated Private Subnet Routing: Deploys a private AWS web server (10.20.1.195) 
that communicates securely with an Oracle Cloud database (10.0.2.37) across the VPN 
tunnel using automated SSH ProxyCommand bastion routing.

Web Application & WAF Protection: Deploys a Python Flask application behind an 
Nginx reverse proxy fortified with an inline ModSecurity WAF configured with 
explicit SQL injection detection rules.
