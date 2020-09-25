## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/ELKAzureTAD(Last).DRAWIO

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. 
Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

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

- What aspect of security do load balancers protect?
Load Balancers help distribute traffic evently among servers, mitigating DoS attacks. It also work as a health probe function, checking regularly to make sure all of the 
machines behind the load balancer are functioning before sending any traffic to it. This function allows the system to don't have downtime for customers, and engineers to
fix any issues seamless.

-What is the advantage of a jump box?
One of the advantage of jump boxes are that, while focusing traffic through a single node, it makes it easier to implement routing logic and design networks. 
Additionally, It controls access to the other machines by allowing connections from specific IP addresses and forwarding to those machines, allowing other machines to
have denied public access, making them more secured. Lastly, by limiting connections and root access through the jumpbox, you can make sure a keep better tracking of allowing
only necessary users to have certain permissions. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the configuration and system files.
- What does Filebeat watch for?
Filebeat watch for log files.
- What does Metricbeat record?
It records system-level data, like CPU usage, memory, disk IO, network IO statistics, processes, etc.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| WEB-1    |Web Server| 10.1.0.5   | Linux            |
| WEB-2    |Web Server| 10.1.0.6   | Linux            |
| WEB-3    |Web Server| 10.1.0.7   | Linux            |
| ELK      |elk Server| 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 24.212.188.212

Machines within the network can only be accessed by the Ansible container.
-  Which machine did you allow to access your ELK VM? What was its IP address?
Jump Box - 10.1.0.4


A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses                         |
|----------|---------------------|----------------------------------------------|
| Jump Box | Yes                 | 10.1.0.5 10.0.0.6 10.1.0.7 24.212.188.212    |
| Web-1    | No                  | 10.1.0.4                                     |
| Web-2    | No                  | 10.1.0.4                                     |
| Web-3    | No                  | 10.1.0.4                                     |
| ELK      | Yes                 | 10.1.0.4  24.212.188.212                     |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the ansible playbooks can be reused 
if we wish to create and configure more servers in the future making configuration consistent. 

The playbook implements the following tasks:
- install docker io
- install python
- install the dovler module
- increase virtual memory
- download and launch the elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- FileBeats
- MetricBeats

These Beats allow us to collect the following information from each machine:
- FileBeats collect logs from the system file changes, like server.log. MetricBeatscollects the metrics of the system, as CPU utilization, processes, etc.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to the /etc/ansible directory.
- Update the ansible config file to include the target
- Run the playbook, and navigate to login page (kibana) to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? Host. How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- _Which URL do you navigate to in order to check that the ELK server is running?