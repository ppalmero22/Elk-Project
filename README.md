## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ELK Project drawio (1)](https://user-images.githubusercontent.com/101301863/158487634-932662b7-daa8-436f-bd6a-6dcbf5cc5e74.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

----

## Playbook Files

- [DVWA-Playbook](https://github.com/ppalmero22/Elk-Project/blob/main/Ansible/playbook.yml)
- [Elk-Install Playbook](https://github.com/ppalmero22/Elk-Project/blob/main/Ansible/install-elk.yml)
- [Metricbeat Install Playbook](https://github.com/ppalmero22/Elk-Project/blob/main/Ansible/metricbeat-playbook.yml)
- [Filebeat Install Playbook](https://github.com/ppalmero22/Elk-Project/blob/main/Ansible/filebeat-installation-playbook.yml)

---

This document contains the following details:
- [Description of the Topology](https://github.com/ppalmero22/Elk-Project#description-of-the-topology)
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system authentication.

### What does Filebeat watch for?

- Monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. It has two main components, inuts and harvesters. They work together to tail files and send event data to the output that you specify. 

### What does Metricbeat record?
  
- It helps monitor the servers by collecting metrics from the system and serices running on the server. It inserts the collected metrics directly into Elasticsearch or send them to Logstash. 
---

The configuration details of each machine may be found below.

| Name     | Function      | IP Address | Operating System |
|----------|---------------|------------|------------------|
| Jump Box | Gateway       | 10.0.0.1   | Linux            |
| ELK      | Monitoring    | 10.1.0.4   | Linux            |
| Web-1    | Web Server    | 10.0.0.8   | Linux            |
| Web-2    | Web Server    | 10.0.0.9   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk-Project machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- 20.228.226.223

Machines within the network can only be accessed by Workstation and JumpBox.

- Which machine did you allow to access your ELK VM? 

  Jump-Box

- What was its IP address?
 
  10.0.0.4 (Private)

A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses       |
|-------------|---------------------|----------------------------|
| Jump Box    | Yes/No              | 10.0.0.1  20.228.226.223   |
| Web-1       | No                  | 10.0.0.8                   |
| Web-2       | No                  | 10.0.0.9                   |
| ELK-Project | No                  | 10.1.0.4   20.110.80.233   |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- It simplifies writing the complex playbook and it easier to reuse. There is no special coding skills needed, tasks executes in order and get productive quickly. There is also less room for user or administrator error.

### The playbook implements the following tasks:  

- Create a new VM 
- Create a yml file
- Install docker.io
- Install python3
- Install docker
- Install the elk container and run “ansible-playbook install-elk.yml”

---

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


![Docker](https://user-images.githubusercontent.com/101301863/158501261-40ff2493-b4d2-47b4-adec-d63a0392b9a3.JPG)


### Target Machines & Beats

This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.8
- Web-2 10.0.0.9

We have installed the following Beats on these machines:

- Metricbeat
- Filebeat

These Beats allow us to collect the following information from each machine:

- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:

- Copy the filebeat-playbook.yml file to /etc/ansible/roles.
- Update the filebeat-config.yml file to include the ELK server private IP in lines 1106 and 1806.
- [ELK public IP] :5601/app/kibana
