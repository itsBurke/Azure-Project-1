# Azure-Project-1

### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.







These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the **my_first_playbook.yml** file may be used to install only certain pieces of it, such as Filebeat.
      
This document contains the following details:
   
   • Description of the Topology
    
   • Access Policies 
   
   • ELK Configuration 
        
        ◦ Beats in Use 
        
        ◦ Machines Being Monitored 
   
   • How to Use the Ansible Build 

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the **application** will be highly available, in addition to restricting **the number of access points** to the network.
      
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **logs** and **system metrics**.
      
The configuration details of each machine may be found below. 

| Name    |Function | IP Address | Operating System |
| ---|--- | --- | --- |
| Jump Box | Gateway | 10.0.0.4 | Linux |
| Web-1 | Web Server | 10.0.0.6 | Linux |
| Web-2 | Web Server | 10.0.0.9 | Linux |
| Web-3 | Web Server | 10.0.0.10 | Linux |
| ELK | ELK Container | 10.1.0.4 | Linux |


### Access Policies

The machines on the internal network are not exposed to the public Internet.

Only the **Jump Box** machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
    
   • **71.204.111.86 (local ip)**

Machines within the network can only be accessed by **SSH from the Ansible container within the Jump Box**.
      
A summary of the access policies in place can be found in the table below.

| **Name | Publicly Accessible | Allowed IP Addresses** |
| --- | --- | --- |
| Jump Box | Yes | 71.204.111.86 |
| Web-1 | No | 10.0.0.1-254 |
| Web-2 | No | 10.0.0.1-254 |
| Web-3 | No | 10.0.0.1-254 |
| ELK | No | 10.0.0.1-254 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
    
   • Ansible can be to update many servers at the same time. It is relatively easy to learn and writes its playbooks in YAML, which make it great for configuration management and automation.

The playbook implements the following tasks:
    
   • Install docker.io
    
   • Install python3-pip
    
   • Install Docker module
    
   • Increase virtual memory
    
   • Use more memory
    
   • Download and launch a docker elk container

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.


### Target Machines & Beats

This ELK server is configured to monitor the following machines:
    
   • **10.0.0.4, 10.0.0.6, 10.0.0.9, 10.0.0.10** 

We have installed the following Beats on these machines:
    
   • **Filebeats and Metricbeats**
   
These Beats allow us to collect the following information from each machine:
    
   • **Filebeats monitors the log files, collects log events, and forwards the data to either           Elasticsearch or Logstash for archiving. It will monitor the syslogs from each host**.
    
   • **Similary, Metricbeats collects metrics from your OS and services running on your servers and sends the output to Elasticsearch or Logstash. An example would be taking statistics from Apache to upload on Elasticsearch**.

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:
    
   • Copy the **install-elk.yml** file to **/etc/ansible**. 
   
   • Update the **hosts** file to include... 
  
   • Run the playbook, and navigate to **http://20.57.1.47:5601/app/kibana#/home** to check that the installation worked as expected. 
       


As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc.
    
   • ansible-playbook install-elk.yml
    
   • nano (playbook name) to update or change file
    
   • nano into config files for filebeat and metricbeat to change the host IP in Kibana and Elasticsearch to ELK server ip 10.1.0.4
