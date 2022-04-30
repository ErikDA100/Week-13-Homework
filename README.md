# Week-13-Homework---
  
  These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.
  
  - name: Config Web VM with Docker
    hosts: webservers
    become: true
    tasks:

    - name: docker.io
      apt:
        update_cache: yes
        name: docker.io
        state: present

    - name: Install pip3
      apt:
        name: python3-pip
        state: present

    - name: Install Python Docker Module
      pip:
        name: docker
        state: present

    - name: download and launch a docker web container
      docker_container:
        name: dvwa
        image: cyberxsecurity/dvwa
        state: started
        restart_policy: always
        published_ports: 80:80
        This document contains the following details:

Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build
Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the DVWA Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting access to the network. -Load balancer provides DDOS and redundancy protection. What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system files.

Installed filebeat to watch for changes in the system and log files.
Instaled metricbeat to record metric's from each VM in the network.
The configuration details of each machine may be found below.

Name	Function	IP Address	Operating System
Jump Box	Provisioner 20.40.65.65	
Web 1	VM	10.0.0.5	
Web 2	VM	10.1.0.6

My computer have my loan balancer 20.92.240.173 and I have my Red Team Network 10.1.0.0/24 and Red Team Resource Group 10.1.0.0/16

Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses

Target Machines & Beats
This ELK server is configured to monitor the following machines:

10.1.0.5
10.1.0.6

We have installed the following Beats on these machines: -fileebeat 7.6.1 -metricbeat 7.6.1

These Beats allow us to collect the following information from each machine:

Filebests allows us to collet agent.host files and other system logs that change for any reason. The mectricbeats collects and logs host system metric's such as operating sysem and other system status's.

Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the install-elk.yml file to Ansible instance.
Update the hosts file to include elk serever
Run the playbook, and navigate.

Diagrams/SECURITY TAREA.png
