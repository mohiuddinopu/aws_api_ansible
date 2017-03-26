# aws_api_ansible

This Ansible Playbook creates ssh key, security group, applies security rules for port 22 and 80 and creates the given number of ec-instances. 

To get started, 

1. Install Ansible 

Linux 

sudo easy_install pip
sudo pip install ansible

Unix

brew install ansible


It suggested to run Ansible master server in Linux or Unix machine. Installing and running Ansible master in Windows is fairly complex. One can follow this tutorial to do so. 

https://www.jeffgeerling.com/blog/running-ansible-within-windows


Test Ansible installation

In command line, 
  ansible --version 
  
This should produce similar outout 

Output
ansible 2.1.1.0
  config file =
  configured module search path = Default w/o overrides
  
  
To run this playbook, from command line, 

git clone https://github.com/mohiuddinopu/aws_api_ansible.git
cd aws_api_ansible
ansible-playbook ansible_deploy_ec2-instances.yml


