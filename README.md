# devops-lab-7th
### ✅ Step 1: Install WSL (Windows Subsystem for Linux)

Run the following in **PowerShell as Administrator**:

```bash
wsl --install
```
✅ Step 2: Launch Ubuntu and Install Ansible
Open Ubuntu from the Start menu and run:

```bash
sudo apt update
sudo apt install ansible -y
```
✅ Step 3: Verify Ansible Installation
```bash
ansible --version
```
Step 4: Create Project Directory
```bash
mkdir ~/ansible-lab
cd ~/ansible-lab
```
Step 5: Create Inventory File
Create a file named hosts:
```
nano hosts
```
```bash
[local]
localhost ansible_connection=local
```
Create a file named install_nginx.yml:
```
nano install_ngnix.yml
```
yml file
```
---
- name: Install and start NGINX on localhost
  hosts: local
  become: yes

  tasks:
    - name: Install NGINX
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Ensure NGINX is running
      service:
        name: nginx
        state: started
        enabled: yes
```
Run:
```
ansible-playbook -i hosts install_nginx.yml
```
Verify 
```
curl http://localhost
```


