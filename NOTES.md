# Ansible Web Server Automation on AWS  Notes  Follow below step 

<img width="1362" height="672" alt="image" src="https://github.com/user-attachments/assets/427ef7c4-fc01-4779-a89f-888b0ed425a3" />


## 1. Create Project Directory

Command 1
mkdir ~/ansible-lab
cd ~/ansible-lab


Purpose:
Create a project folder and move into it.

---

Command 2. Create Inventory File


nano inventory


Content:

 ini
[web]
54.90.119.44 (This is public IP when create EC2 on AWS )  


Purpose:
Store target server details for Ansible.



Command 3. Test SSH Connection


ssh -i ~/win.pem ec2-user@54.90.119.44



Purpose:
Connect to AWS EC2 instance using PEM key.
win.pem when you created EC isntance 
---

Command 4. Install Apache on EC2


sudo dnf install httpd -y


Purpose:
Install Apache web server.

---

Command  5. Start Apache Service


sudo systemctl start httpd
sudo systemctl enable httpd


Purpose:
Start Apache and enable it after reboot.

---

command 6. Check Apache Status


sudo systemctl status httpd


Purpose:
Verify that Apache is running.

---
command 7. Create Website Page


nano index.html


Purpose:
Create custom web page content.

command 8. Create Ansible Playbook


nano deploy-web.yml


Purpose:
Automate website deployment.

Example:

yaml

  name: Deploy Website
  hosts: web
  become: yes

  tasks:
    - name: Copy index page
      copy:
        src: index.html
        dest: /var/www/html/index.html
```



command 9. Test Ansible Connectivity


#ansible all -i inventory -m ping -u ec2-user --private-key ~/win.pem


Purpose:
Verify Ansible can reach the server.

Expected Output:

ping: pong


---

Command 10. Run Playbook


#ansible-playbook -i inventory deploy-web.yml -u ec2-user --private-key ~/win.pem


Purpose:
Deploy website automatically.


Command 11. Restart Apache


$sudo systemctl restart httpd


Purpose:
Apply website changes.

---

Commans 12. Simulate Service Failure


$sudo systemctl stop httpd


Purpose:
Practice troubleshooting.

---

Command 13. Recover Service


$sudo systemctl start httpd


Purpose:
Restore website availability.

---
Command 14. Check Website

Open browser:

text
http://PUBLIC-IP  teke from EC2 


Purpose:
Verify successful deployment.

---

Command 15. Initialize Git Repository


git init


Purpose:
Start version control.

---

Command 16. Add Files


git add .


Purpose:
Stage project files.

---

Command 17. Commit Changes


git commit -m "Initial commit"


Purpose:
Save project snapshot.

---
command 18. Connect GitHub Repository


git remote add origin repository url


Purpose:
Link local project with GitHub.

---

Command 19. Push Code


git branch -M main
git push -u origin main


Purpose:
Upload project to GitHub.

---

## Skills Practiced

* AWS EC2
* Linux Administration
* SSH Authentication
* Apache Web Server
* Ansible Inventory
* Ansible Playbooks
* Configuration Management
* Infrastructure Automation
* Troubleshooting
* Git & GitHub
* DevOps Fundamentals


