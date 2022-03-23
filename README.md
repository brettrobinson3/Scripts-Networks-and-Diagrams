## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
-Diagrams/Resource Group Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - ansibleplaybook.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly flexible and efficient, in addition to restricting access to the network.
-Load Balancers prevent the servers from being overloaded by distributing the traffic across multiple servers. A jump box allows you to control the servers in a scalable way.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.
-Filebeat organizes log data so it can be easily read and shared.
-Metricbeat organizes the servers' metric data into an easily readable formats

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web1     | Webserver| 10.0.0.5   | Linux            |
| Web2     | Webserver| 10.0.0.6   | Linux            |
| Web3     | Webserver| 10.0.0.7   | Linux            |
| ElkVM    | Container| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-72.197.249.183

Machines within the network can only be accessed by the Jump-Box.
-52.191.76.38

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 72.197.249.183       |
| ElkVM    | No                  | 10.0.0.4             |
| Web1/2/3 | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The main advantage of automating configuration is the scalability and efficiency it provides.

The playbook implements the following tasks:
-Install Docker.io
-Install python3-pip
-Install Docker module
-Download and Launch a Docker ELK container
-Enable Docker service on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Diagrams/elk docker screenshot.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-10.0.0.5
-10.0.0.6
-10.0.0.7

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat allows us to collect system logs from each server and Metricbeat allows us to see metrics of how the docker containers are processing information.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ansible host file to /etc/ansible.
- Update the host file to include the internal IP addresses of your webservers and ELK server.
- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
-Which file is the playbook? Where do you copy it?
We copy this to our virtual machines.
-Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
This is specified in the configuration file.
-Which URL do you navigate to in order to check that the ELK server is running?
You navigate to the public IP address of your elk server using the port 5601
<ELK-IP-ADDRESS>:5601
