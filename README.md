# ELK
Elk server project

## Automated ELK Stack Deployment

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

  - The ansible playbooks & filebeat-playbook-webservers.yml & elk-docker.yml are needed to create and deploy the Elk server.

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

- What aspect of security do load balancers protect?_
	
	Load balancers protect the availability aspect of security.

- What is the advantage of a jump box?_
	
	The advantage of a jump box is being able to access and manage different machines by allowing connections from specific IP addresses.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.

- What does Filebeat watch for?_

	Filebeat watches for log files/locations and collects log events
- What does Metricbeat record?_

	Metricbeat records metric and statistical data from the operating system and from services running on the server







The configuration details of each machine may be found below.


| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.1.0.5   | Linux            |
| Web-1    | DockerDVWA| 10.1.0.6   | Linux            |
| Web-2    | DockerDVWA| 10.1.0.7   | Linux            |
| ELK      | ELK-Kibana| 10.0.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 52.149.230.168

Machines within the network can only be accessed by SSH from within the Jump-Box-Provisioner.

- Must be connected to the Jump-Box then use the private IP to SSH into the ELK server.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 52.149.230.168       |
| Web-1    | No                  | 10.1.0.6             |
| Web-2    | No                  | 10.1.0.7             |
| ELK      | No                  | 10.0.0.4             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _You can write one playbook and configure multiple machines using a single command. 

The playbook implements the following tasks:
- Using the machines stated in host file
- installs docker.io & python3-pip docker
- increase memory
- download ELK over certain ports


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web 1: 10.0.0.6
- Web 2: 10.0.0.7

We have installed the following Beats on these machines:

- Installed filebeat onto the Web 1 and Web 2 servers; the logging information is being sent to the Elk server.

These Beats allow us to collect the following information from each machine:

-	The filebeat allows us to collect and log files or locations that are specified, and forwards them for indexing. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Update the configuration file to include the private IP of the Elk server 
- Run the playbook,and navigate to the Elk server public IP address (http://52.158.244.29:5601/app/kibana) to check that the installation worked as expected.

To run the Ansible configuration for ELK: 
 - ssh azdmin@52.149.230.168 
 - runthe commands:
 - sudo docker containter list -a (locate name of container) [thirsty_wozniak]
 - sudo docker start thirsty_wozniak
 - sudo docker attach thirsty_wozniak
 - sudo docker ps (check status)
 - cd /etc/ansible (elk-docker.yml) 
 - cd /etc/ansible/roles (filebeat-playbook.yml)
 - web page: http://52.158.244.29:5601/app/kibana to reach kibana portal
