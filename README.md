# Infastructure as Code Using Ansible
- 1.[What is IAC?](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/README.md#what-is-iac)
- 2.[Ansible](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/README.md#ansible)
- 3.[Ad-hoc Commands](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/README.md#ad-hoc-commands)
- 4.[Playbooks](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/README.md#playbooks)

## What is IAC?
- IaC is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools
- Infrastructure as Code (IaC) uses a high-level descriptive coding language to automate the provisioning of IT infrastructure. This automation eliminates the need for developers to manually provision and manage servers, operating systems, database connections, storage, and other infrastructure elements every time they want to develop, test, or deploy a software application.

### The types of Infastructure
- They can be Mutable or Immutable
- Run from local or run from the cloud

### Two parts of IaC
#### Configuration Management
Tools that are responsible for provisioning and maintaining the state of your systems. Some common configuration management tools are:
- Chef
- Puppet
- Ansible

#### Orchestration
Once we've created the templates for all the parts of the system, we can use orchestration tools and scripts that toalk to the cloud to pull them together into the architecture. Common orchestration tools:
- Cloudformation
- Ansible
- Terraform

### Benefits of IAC
- Efficiency is increased in the software development lifecycle
- Cost savings
- Speed and simplicity
- It is much more consistent
- Minimization of risk

### The Best Practices
- Codify everything
- Document as little as possible
- Maintain version control
- Continuously test, integrate and deploy
- Make your infrastructure code modular
- Make your infrastructure immutable (when possible, nobody can go in and change it without your permission)

## Ansible 
Ansible is an open-source software that includes:
- software provisioning
- configuration management
- application-deployment tool
- intra-service orchestration enabling infrastructure as code

### What are the benifits?
- It is **Simple** - uses YAML (Yet Another Markup Language), so it's human readable
- It is **Agentless** - makes it lightweight on agent nodes, no need to install in agent notes
- It is **Secure** - uses SSH to connect to other servers
- It is **Efficient** - Integrates with other tools, We can change provider very easily.

#### Diagram 
- **Diagram of Ansible flow**
![ansible_diagram](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/Images/Ansible_diagram.png?raw=true)
- **Diagram of Our Anisible we are working on**
![ansible_flow](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/Images/Ansible_flow.png?raw=true)

## Ad-hoc Commands
Adhoc commands can be used to run commands in other servers from the Ansible controller.

- ssh vagrant@server_ip - SSH into another vagrant machine
- hosts file holds info to configure with the other servers (stored in /etc/ansible directory)
- Adding a web host in the hosts file:
  ```
  [web]
  192.168.33.10 ansible_connection=ssh ansible_ssh_user=vagrant ansible_ssh_pass=vagrant
  ```
  
### Commands for Ansible
- `-m` - specifies a module
- `-a` - an adhoc
- ``ansible web -m ping`` - ping into the web server
- ``ansible all -m ping`` - ping all the machines
- ``ansible web -a "uname -a"`` - find out machince 
- ``ansible web -a "date"`` - find out date on web server 
- ``ansible web -a "free -m"`` - display available memory in web server
- ``ansible web -m shell -a "ls -a"`` - list all files in web server 
- ``sudo nano hosts`` - This lets us edit the host file with admin permissions 

#### Task
- ``ansible db -m shell -a "uptime"`` - uptime for the database
- ``ansible all -m shell -a "sudo apt-get update -y"`` - update Linux on all machines
- ``ansible all -m shell -a "sudo apt-get upgrade -y"`` - upgrade Linux on all machines

## Playbooks
- Playbooks are configuration files used to run commands that are often used.
- Same location as the hosts file (/etc/ansible)
- **Indentation is VERY important when using Ansible**

### Making playbook files:
``sudo nano install_nginx.yml`` - we use this command to create a YAML file, in this case we are installing Nginx
``ansible-playbook install_nginx.yml`` - run the YAML file

## Our IAC using AWS
### Diagram 
![IAC_aws](https://github.com/ArunPanesar42/IAC_with_Ansible/blob/main/Images/Diagram%206may.png?raw=true)
### Scaling features with AWS

