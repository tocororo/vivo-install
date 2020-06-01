# Ansible Project
This is an open source project in which the community can suggest changes, take it and adapt it to their environment and needs.
Some community roles have been taken and updated in this context, others have been created in this context. The goal is to create a project to install and manage any instance of VIVO with all possible configurations over time

## Requirements
This project has been tested on Ubuntu 18.04. You also need internet connection to install all packages.
Java 8 OpenJDK as its minimum version, Maven to manage installation packages, MySQL as SQL database, Tomcat 7 or higher as web server and Solr for search indexes. Furthermore, access to the Ubuntu repositories is necessary for the correct installation of the aforementioned systems.

## Steps on the master server
1. Install Ansible on the master server. For other installation methods, see the [Ansible documentation](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

        $ pip install –user ansible

2. Install Git version control

        $ apt install git

3. Clone the VIVO installation repository

        $ git clone https://gitlab.upr.edu.cu/VIVO/vivo-install.git

4. Create, if it does not exist, a public key to connect Ansible with the nodes

        $ ssh-keygen

## Steps on node servers
1. Copy the public key to all hosts by the means that you create convenient

2. Create, if it does not exist, the ".ssh" folder

        $ mkdir –p /root/.ssh

3. Located in the folder where you copied the public key, add it to the authorized_keys by running

        $ cat “my_public_key.pub” >> /root/.ssh/authorized_keys

4. Check that you can access the hosts from the master by running

        $ ssh root@”host_ip”

## Steps to install
1. edit the "vivo" and "mysql" files in the "group_vars" folder to adjust it to your needs

2. edit the "production" file in the inventory folder and modify the IP addresses. `IMPORTANT`, do not change the names that appear in square brackets

3. In the master console, move to the "playbook" folder and execute the following command

        $ ansible-playbook vivo.yml

## License

MIT / BSD

## Authors

- [Centro  de Recursos para el Aprendizaje y la Investigación de la Universidad de Piniar del Río Hermanos Saiz Montes de Oca](https://crai.upr.edu.cu)
- [Proyecto Tocororo](https://tocororo.upr.edu.cu)