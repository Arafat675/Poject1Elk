## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
 ![alt text](https://github.com/Arafat675/Poject1Elk/blob/main/Images/Network%20Diagram.png)

 


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of theAnsible playbook files may be used to install only certain pieces of it, such as Filebeat.

  [filebeat-playbook.yml](https://github.com/Arafat675/Poject1Elk/blob/main/Ansible/filebeat-playbook.yml)
  
  [filebeat-configuration.yml](https://github.com/Arafat675/Poject1Elk/blob/main/Ansible/filebeat-configuration.yml)
  
  [metricbeat-playbook.yml](https://github.com/Arafat675/Poject1Elk/blob/main/Ansible/metricbeat-playbook.yml)
  
  [metricbeat-configuration.yml](https://github.com/Arafat675/Poject1Elk/blob/main/Ansible/metricbeat-configuration.yml)
  
  
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will have high availability, in addition to restricting the loadt to make a network more efficient.
load balancers also can defelct DDoS attacks. Jump boxes are also a great option because they will prevent all the machines on a network from being exposed.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system Traffic.
File Beat will monitor logs, collect logs and can forward them so they can be indexed.
 Metricbeat records metrics like cpu usage and other metric data.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name  | Function  | IP Address  | Operating System |
|---      |---        |---        |---             |
|jumpbox  |Gateway    |10.0.0.4   |Linux           |
| web1    |Web Server |10.0.0.5   |Linux           |
| web2    |Web Server |10.0.0.6   |Linux           |
| web3    |Web Server |10.0.0.7   |Linux           |
| ElkSer  | Elk Stack |10.1.0.4   |Linux           |



Machines within the network can only be accessed by the jumpbox.
- only the jump box can accpet network traffic from the internet. the only way to access it is from my personal workstaion.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | Home IP              |
| web1     | No                  | 10.0.0.4             |
| web2     | No                  | 10.0.0.4             |
| web3     | No                  | 10.0.0.4             |
| ElkSer   | No                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
it very simple to setup and use
The playbook implements the following tasks:
installs docker,python3-pip,docker module for pip
Setups systemctl
downloads and lauches the elk container 

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
web1 10.0.0.5
web2 10.0.0.6
web3 10.0.0.7
We have installed the following Beats on these machines:
Filebbeats
Metricbeats

These Beats allow us to collect the following information from each machine:
Filebbeats- collects system logs witch can tracked and monitored.
Metricbeats- Collects system data like cpu usage and other metrics
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
-Copy the filebeat and metricbeat config files to /etc/ansible//.
- Update thethe config files to your Elk server's private IP adress, for the filebeat lines 1106 and 1806 for metric beat lines 62 and 96 
- Run the playbook, and navigate to http://[ELK-server-public-IP]:5601/app/kibana to check that the installation worked as expected.
filebeat-playbook.yml is the playbook, copy it to /etc/ansible/
To run the playbook on a specifiv machine you can update /etc/ansible/hosts file
You can go to this URL http://[ELK-server-public-IP:5601]/app/kibana to confrim if your elk server is running


