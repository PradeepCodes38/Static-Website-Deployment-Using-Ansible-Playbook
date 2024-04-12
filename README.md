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



-----------------------------------------------


# The ansible-galaxy role init command is used to initialize a new Ansible role directory structure. This command creates a standard directory layout with predefined subdirectories and files, making it easier to organize and manage your Ansible roles.

$ ansible-galaxy role init
Example:- ansible-galaxy role init kubernetes

# This command will create a directory structure for your Ansible role "kubernetes" with the following subdirectories and files:

        kubernetes/: Root directory for the role.
    defaults/: Directory for default variable files.
    files/: Directory for static files that can be copied to hosts.
    handlers/: Directory for handler tasks.
    meta/: Directory containing metadata for the role.
    tasks/: Directory for main tasks of the role.
    templates/: Directory for Jinja2 template files.
    tests/: Directory for test-related files.
    vars/: Directory for variable files.
    README.md: Readme file with information about the role.
    LICENSE: License file for the role (e.g., MIT, GPL).
    CHANGELOG.md: Changelog file for tracking changes to the role.


