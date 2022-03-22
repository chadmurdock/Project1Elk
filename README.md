## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/chadmurdock/Project1Elk/blob/main/Diagrams/Network%20Diagram%20with%20Elk.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

https://github.com/chadmurdock/Project1Elk/blob/main/Ansible/filebeat-playbook.rtf

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
What aspect of security do load balancers protect? Load Balancers ensure availability and protect an organization from DDos attacks by distributing network traffic across multiple servers. What is the advantage of a jump box? A jump box acts as a single point of access to machine(s) within the network, therefore increasing security as both incoming and outgoing traffic within the network can be monitored through a single point. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system log files and system usage.
What does Filebeat watch for? Filbeat watches log files and log events.
What does Metricbeat record? Metricbeat records CPU usage, memory resident set size, and memory usage, as well as, other statistics for processes that are funning on the system that is being monitored. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Elk      | Logging  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP 136.36.120.46

Machines within the network can only be accessed by Jumpbox Provisioner.
Which machine did you allow to access your ELK VM? What was its IP address? 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes.                | 136.36.120.46.       |
| Web-1/2  | No                  | 10.0.0.4             |
| Elk      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...  
What is the main advantage of automating configuration with Ansible? Anisble improves efficiency, management, and scalability by allowing you to manage all of your servers in one instance instead of managing each server individually.

The playbook implements the following tasks:
In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker allowing for the installation of the containers
- Install python3-pip
- Install the docker and python module
- increase your virtual memory on the machine
- download and launch the docker Elk container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/chadmurdock/Project1Elk/blob/main/Ansible/docker-ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring 10.0.0.5 and 10.0.0.6

We have installed the following Beats on these machines:
Specify which Beats you successfully installed Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine: 
Filbert collects log and file data which is used to monitor and track unusual behavior. 
Metricbeat collects metrics to help with the assessment about the operational state of the machines on the network and sends it to Elasticsearch on Elk. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to Ansible folder.
- Update the host file to include the Elk server IP address of 10.1.0.4.
- Run the playbook, and navigate to http://20.119.52.149:5601/app/kibana to check that the installation worked as expected.

Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? /etc/ansible/files
- Which file do you update to make Ansible run the playbook on a specific machine? Hosts file How do I specify which machine to install the ELK server on versus which to install Filebeat on? Specify the webservers. 
- Which URL do you navigate to in order to check that the ELK server is running? http://20.119.52.149:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
1. SSH into the JumpBox Provisioner (ssh username@jumpboxIP)
2. Start and then attach to your Ansible container (sudo docker start container "name of container" & then run sudo docker attach "name of container")
3. run nano /etc/ansible/hosts (edit this by adding [elk] as a group so that ansible can discover it and then connect to it)
4. cd /etc/ansible to create the yml file in order to install elk 
5. touch install-elk.yml The following yml scripts and config files can be seen in the link below:
