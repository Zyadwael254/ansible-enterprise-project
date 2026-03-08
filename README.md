# ansible-enterprise-project
ansible-enterprise-project

# AWS Multi-Tier Infrastructure Automation with Ansible

## Project Overview
This project demonstrates a professional-grade automation of a secure, scalable infrastructure on AWS. It uses **Ansible Roles** to manage a multi-tier architecture consisting of a Bastion host and private nodes.

## Network Architecture
- **Bastion Host (Jump Server):** Public-facing instance for secure SSH tunneling.
- **Load Balancer (HAProxy):** Distributes traffic across web servers in a private subnet.
- **Web Servers (Apache):** Hosted in a private subnet for enhanced security.

## Features
- **Security-First:** All private nodes are accessed via SSH ProxyCommand through the Bastion host.
- **Modular Design:** Infrastructure is managed using decoupled Ansible Roles (`common`, `webstack`, `loadbalancer`).
- **Standardization:** Automated system updates and installation of networking tools (`net-tools`, `ufw`, `curl`).

## Directory Structure
- `ansible.cfg`: Configured for SSH ProxyCommand.
- `inventory.ini`: Defined host groups and private IP routing.
- `roles/`:
  - `common`: System hardening and base utilities.
  - `webstack`: Apache installation and custom dynamic landing pages.
  - `loadbalancer`: HAProxy configuration for Round Robin distribution.

## How to Deploy
1. Update `inventory.ini` with your AWS Private IPs.
2. Add your `.pem` key to the SSH agent: `ssh-add ~/key.pem`.
3. Run the playbook: `ansible-playbook site.yml`.
