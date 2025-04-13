# Ansible-Automation
This project tackles Ansible automation challenges on Ubuntu 24.04 (especially in WSL environments without systemctl). 

# Challenge: Working with Ansible  
This task was tested on a **Ubuntu 24.04 VM**. Key challenges arose due to:  
- Lack of `systemctl` in **WSL-based Linux** environments.  
- The requirement to connect via **`localhost`** for VM access.  

# Key Issues  
1. **Ansible Authentication**:  
   - Ansible no longer supports cloning private Git repositories via *username/password*.  
   - **SSH keys** or **GitHub Personal Access Tokens (PAT)** are now required.  

Permission Errors**:  
   - Public repositories clone without issues, but private repositories throw `Permission Denied` errors.  


# Solution Steps  

Generate and Configure SSH/PAT:  
- Create a **PAT** (Private Access Token) from GitHub.  
- Use Ansible’s built-in `decrypt` feature to securely handle the token.  
- Define the token or SSH key as an **environment variable** in `vars/main.yml`.  

![ezgif com-video-to-gif-converter(1)](https://github.com/user-attachments/assets/2432a158-74aa-4a31-9d89-5898c2819cbb)


# Playbook Configuration:  
- The `deploy.yml` playbook uses the token/key to authenticate and clone repositories.  
- A commented section in the code demonstrates key setup (see `deploy.yml`).  

# Service Management:  
- After transferring files (e.g., a Python script), a `test.service` file is created.  
- The service is activated manually (due to `systemctl` limitations in WSL).  


# mplementation Details  
- **Code Reference**:  
  - `deploy.yml`: Handles authentication and deployment.  
  - `test.service`: Manages the service setup.  
- **Video Demo**: A test video shows the SSH key setup, Ansible authentication, and service activation.  

![ezgif com-video-to-gif-converter](https://github.com/user-attachments/assets/559b2d88-dce5-4c14-af05-422563aa12c4)


# Source & Inspiration:  
For the atomic deployment approach, see [mahmudasif.com/atomic](https://mahmudasif.com/atomic).  
