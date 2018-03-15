# Steps to Getting started with Ansible 
## Step 1 - install Ansible on the Control Machine
	- $sudo apt-get update
	- $sudo apt-get install software-properties-common
	$sudo apt-add-repository ppa:ansible/ansible
	$sudo apt-get update
	$sudo apt-get install ansible
	
## Step 2 - configure the Host file
	-configure the inventory file, you can find the default one on this location $cd /etc/ansible/hosts
	-Add the IP of Managed Node in the hosts file

## Step 3 - Prepare the key
	-Copy the private key.pem into the control machine 
	-$chmod 400 key.pem

## Step 4 - Check the connection between the control machine and the managed node
	-To check the connection between the contol Machine and the Managed Node ==> $sudo ansible all -m ping --private-key key.pem --user=ubuntu -e 'ansible_python_interpreter=/usr/bin/python3'

## Step 5 - Run Ad-hoc command command
	-To install Nginx ==> $sudo ansible all -s -m shell -a 'apt-get install nginx -y' --private-key key.pem --user=ubuntu -e 'ansible_python_interpreter=/usr/bin/python3'
	
## Step 6 - Run Ansible Ad-Hoc command using Ansible Module
	-Run ansible Module $sudo ansible all -s -m apt -a 'pkg=nginx state=installed update_cache=true' --private-key key.pem --user=ubuntu -e 'ansible_python_interpreter=/usr/bin/python3'
	
## Step 7 - Create a simple playbook 
   ```
   - hosts: local
	  tasks:
		- name: Install Nginx
            apt: pkg=nginx state=installed update_cache=true
   ```
		  
## Step 8 - Run the playbook
	-$sudo ansible-playbook -s nginx.yml --private-key key.pem --user=ubuntu -e 'ansible_python_interpreter=/usr/bin/python3'
