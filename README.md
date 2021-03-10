## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
![Arianna Ommundsen HW 12 (3)](https://user-images.githubusercontent.com/73668221/110558514-a30e1100-8110-11eb-970d-3d178877f085.png)


These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file-beat playbook.yml file may be used to install only certain pieces of it, such as Filebeat.


![install elk](https://user-images.githubusercontent.com/73668221/110512773-81426900-80d3-11eb-9094-3deaa69eddac.JPG)

![file-beat playbook](https://user-images.githubusercontent.com/73668221/110511354-252b1500-80d2-11eb-9a5a-ce2813e4352b.JPG)


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.

-Load balancing ensures that the application will be highly responsive, in addition to restricting traffic to the network.

-The advantage of a Jump Box is that it minimises the attack surface by ensuring remote connections to the cloud network come through a single VM.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system log.
- Filebeat collects and logs data about the file system.
- Metricbeat collects machine metrics.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| ELK      | Server   | 10.1.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.7   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Web-3    | Server   | 10.0.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 13.92.37.104

Machines within the network can only be accessed by Jump Box machine.

-The ELK VM was allowed to access the Jump Box machine and Web1, Web-2 and Web-3. 13.92.37.104 , 10.0.0.7 , 10.0.0.6 , 10.0.0.8.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 10.0.0.1 10.0.0.2    |
| Web-1    | No                  |                      |
| Web-2    | No                  |                      |
| Web-3    | No                  |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-The main advantage of automating configuration with Ansible is that it allows IT administrators the ability to automate your daily work tasks and give the administrator more time to focus on the needs of the business.

The playbook implements the following tasks:
-Configure ELK with Docker
-Install docker.io
-Install pip3
-Download and launch docker in ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.7
- Web-2 10.0.0.6
- Web-3 10.0.0.8

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects and logs data about the file system.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML file to /etc/ansible.
- Update the /etc/ansible/hosts file to include hosts group, private IP adresses and ansible_python_interpreter=usr/bin/python3
- Run the playbook, and navigate to curl localhost/setup.php to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
