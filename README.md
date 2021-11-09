## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/LNKitchell/Designed-and-Deployed-Secure-Cloud-Network-with-ELK-Stack/blob/main/Images/cloud.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly stable, in addition to restricting access to the network.
Load balancing provides a redundancy measure in case of a server failure or a DDoS Attack.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- collects the logs files and sends them to Elasticsearch
- collects metrics from your system and services

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |  DVWA    | 10.0.0.7   | Linux            |
| Web-2    |  DVWA    | 10.0.0.9   | Linux            |
| elk-box  | Gateway  | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBoxProvisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
174.26.22.231

Machines within the network can only be accessed by an ansible container within the Jump Box Provisioner with the correct ssh keys -10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box |     No              | 174.26.22.231        |
| Red-Net  |     No              | 10.0.0.4             |
| elk-box  |     No              | 174.26.22.231        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time creates consitanct and reduces human error
The playbook implements the following tasks:
- use sysctl to increase memory
- Installs: docker.io, python3-pip, and docker python pip module
- Download and install the container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

dockerps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 @10.0.0.7
- Web-2 @10.0.0.9

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat is a log management tool. It collects the logs files and sends them to Elasticsearch
- Metricbeat is used for monitoring. It collects metrics from your system and services.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the Ansible container on the JumpBoxProvisioner.
- Update the Ansible hosts file file to includea header indicating a grouping of machine called "elk" and insert the IP address under elk
- Run the playbook, and navigate to the elk-vm to check that the installation worked as expected.

- URL to navigate to in order to check that the ELK server is running
	- http://20.80.188.192:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
