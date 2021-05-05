# Infastructure as Code Using Ansible


## What is IAC?
IaC is the process of managing and provisioning computer data centers through machine-readable definition files, rather than physical hardware configuration or interactive configuration tools

## Ansible 
Ansible is an open-source

- software provisioning
- configuration management
- application-deployment tool
- intra-service orchestration enabling infrastructure as code

### What are the benifits?
- It is **Simple** - uses YAML (Yet Another Markup Language), so it's human readable
- It is **Agentless** - makes it lightweight on agent nodes, no need to install in agent notes
- It is **Secure** - uses SSH to connect to other servers

### Commands for Ansible
- ``ansible all -m ping``
- ``ansible web -a "uname -a"``
- ``ansible web -a "date"``
- ``ansible web -a "free -m"``
- ``ansible web -m shell -a "ls -a"``
- ``sudo nano hosts``
#### Task
- ``ansible db -m shell -a "uptime"`` - uptime for the database
- ``ansible all -m shell -a "sudo apt-get update -y"`` - update Linux on all machines
- ``ansible all -m shell -a "sudo apt-get upgrade -y"`` - upgrade Linux on all machines
