# Static-Website-Deployment-Using-Ansible-Playbook
Developed an Ansible playbook to automate the deployment of a static website. The playbook installs NGINX, starts the NGINX service, and deploys the website content to the server. Implemented as part of infrastructure automation for efficient and scalable website deployment.

# Only do it After the configuration procedure:

# Create a New Directory File into your ubuntu system.
$ mkdir Playbook ( or your own file name)
$ cd playbook

# Create a YML file :
$ vim install_nginx_play.yml

    Write this command  (proper Indentation otherwise it gives errors)
    
  - name: Install nginx and serve static website
  hosts: servers
  become: yes

  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: latest

  - name: Start nginx
      service:
        name: nginx
        state: started

# Execute it by using:
$ ansible_playbook filename.yml

# Now go to the server Local IP Address Where you hosts.

# For Deploying static Website we have to create a another file:
----Create a index.html file in the host directory using:
$ vim index.html

then , Create

$ vim deploy_static_page_play.yml

      Write this command  (proper Indentation otherwise it gives errors)

  - name: Install nginx and serve static website
  hosts: servers (you can change it acc to your server choice)
  become: yes

  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: latest

  - name: Start nginx
      service:
        name: nginx
        state: started

    - name: Deploy webpage
      copy:
        src: index.html
        dest: /var/www/html

# Execute the Deploy File using:
$ ansible-playbook deploy_static_page_play.yml

# check the Hosts server where you host 
using host local IP address



      


