## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Project1/Diagrams/RedTeamDiagram

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

  - install-elk.yml 
  - filebeat-playbook.yml 
  - filebeat-config.yml
  - install-dvwa.yml
  - metricbeatplaybook.yml
  - metricbeat.yml
  - ansible.cfg
  - hosts

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting traffic to the network.
- They protect availability.  The jumpbox is used to access the private IP's of the web servers.  It is used as a gateway to the network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system metrics.
- Filebeat watches for changes to files within a given system.
- Metricbeat watches for changes to metrics within a given system.  

The configuration details of each machine may be found below.

| Name       | Function  | IP Address | Operating System |
|------------|-----------|------------|------------------|
| RedJumpBox | Gateway   | 10.0.0.4   | Linux            |
| Web-1      | WebServer | 10.0.0.5   | Linux            |
| Web-2      | WebServer | 10.0.0.6   | Linux            |
| Web-3      | WebServer | 10.0.0.7   | Linux            |
| Project1   | ELK Stack | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 24.217.42.98


Machines within the network can only be accessed by RedJumpBox.
- My home network can access the ELK server.  The servers within can be accessed through the ansible container. 

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| RedJumpBox | No                  | My home network      |
| Web-1,2,3  | No                  | RedJumpBox           |
| Project1   | No                  | My home network      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because all systems will be updated and maintained. 

The playbook implements the following tasks:
- Install docker.io
- Install pip3
- Install docker python module
- Use more memory
- Download and launch a docker elk container and enable on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Project1/Ansible/docker_ps_output

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects file changes.   Filelog would log changes made to files. 
- Metricbeat collects metric changes.  Metriclog would log changes made to metrics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to Playbook.
- Update the Hosts file to include ip addresses.
- Run the playbook, and navigate to the container to check that the installation worked as expected.

