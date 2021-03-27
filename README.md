# CyberSecurity
Ansible, Bash Scripts, and Network Diagrams.
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/Network Diagram.draw.io.pdf)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.

| Name       | Function         | IP Address | Operating System |
|------------|------------------|------------|------------------|
| Jump Box   | Gateway          | 10.0.0.4   | Linux            |
| Web-1      | DVWA site server | 10.0.0.5   | Linux            |
| Web-2      | DVWA site server | 10.0.0.6   | Linux            |
| Elk server | ELK stack        | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 174.20.85.246

Machines within the network can only be accessed by Jump Box 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Address     |
|------------|--------------------|-------------------------|
| Jump Box   | Yes                | 174.20.85.246           |
| Web-1      | No                 | 174.20.85.246 10.0.0.4  |
| Web-2      | No                 | 174.20.85.246 10.0.0.4  |
| Elk server | No                 | 174.20.85.246           |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it reduces errors and automates tasks.

The playbook implements the following tasks:
Install docker.io
Install python3-pip
Install Docker module
Increase virtual memory
Use more memory
Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web-1 10.0.0.5
Web-2 10.0.0.6

We have installed the following Beats on these machines:
Web-1 10.0.0.5
Web-2 10.0.0.6

These Beats allow us to collect the following information from each machine:
Filebeat collects file system data and sends it to Elasticsearch. Examples of data we can collect are number and types of downloads, HTTP response codes visitors encountered, how many error codes visitors received, etc. 
Metricbeat collects container information such as machine metrics, system process, uptime and CPU usage. We can use this information to identify interruptions such as network issues and make sure the applications and services meet service-level agreements.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file to the Web VMs.
- Update the playbook yml file to include installing and launching filebeat, downloading the filebeat .deb file, dropping the filebeat configuration file into the web servers, enabling and configuring system modules, setting up filebeat, and starting filebeat. 
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

The playbook is the filebeat-ansible.yml file located in the Ansible container on the Jump Box in etc/ansible/files.
To run the playbook on a specific machine, you update the configuration file. 
To specify which machine to install the ELK server on versus which to install Filebeat on, adjust the configuration and host files. 
To verify the Elk server is running, use a browser to navigate to [ELK-Server_IP]:5601/app/kibana  
