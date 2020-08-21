## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/elk_project_topology.gliffy
## Make sure to iport the file to gliffy to view it!

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select files may be used to install only certain pieces of it, such as Filebeat.
- ELK-install.yml
- filebeat-install.yml
- metricbeat-install.yml


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
_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server metrics and system logs.

-
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function    | IP Address    | Operating System |
|----------|-------------|---------------|------------------|
| Jump Box | Gateway     | 52.149.167.41 | Ubunto 18.04     |
| Web-1    | DVWA Server | 10.0.0.7      | Ubunto 18.04     |
| Web-2    | DVWA Server | 10.0.0.6      | Ubunto 18.04     |
| Web-3    | DVWA Server | 10.0.0.5      | Ubunto 18.04     |
| ELK      | ELK Server  | 20.187.48.224 | Ubunto 18.04     |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box
 machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 76.190.142.142
- 

Machines within the network can only be accessed by the Jump Box 52.149.167.41.
-

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Address       |
|----------|---------------------|--------------------------|
| Jump Box | Yes                 | 76.190.142.142           |
| Web-1    | No                  | 10.0.0.4                 |
| Web-2    | No                  | 10.0.0.4                 |
| Web-3    | No                  | 10.0.0.4                 |
| ELK      | No                  | Port 22 - 10.0.0.4       |
|          |                     | Port 80 - 76.190.142.142 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it can be rapidly redeployed in the even that original server goes down
-

The playbook implements the following tasks:
- Increase virtual memory; a requirement to run ELK properly
- Utilize the increased memory
- install Docker
- install Pip
- install Python Docker module
- download and start ELK

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7
We have installed the following Beats on these machines:
- Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat will allow us to collect system logs such as login records and system alert records.
- Metricbeat will allow us to compile system data such as CPU and Memory usage throughout the day.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the anisible.cfg file to /etc/ansible/.
- Update the hosts file to include monitered machines and the monitering machine groups. You'll specify which group to install the respective programs on in the specific playbook.
- Run the playbook, and navigate to http://20.187.48.224:5600/app/kibana to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_


_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._