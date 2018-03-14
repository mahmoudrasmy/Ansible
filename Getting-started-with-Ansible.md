# Steps to Getting started with Ansible 
## Step 1 - install Ansible on the Control Machine
	
	$sudo apt-get update
	$sudo apt-get install software-properties-common
	$sudo apt-add-repository ppa:ansible/ansible
	$sudo apt-get update
	$sudo apt-get install ansible
	
## Step 2 - configure the Host file
	-configure the inventory file, you can find the default one on this location $cd /etc/ansible/hosts
	-Add the IP of Managed Node in the hosts file

## Step 3 - Prepare the key
	-Copy the private key.pem into the control machine 
	-$chmod 400 key.pem
	-To check the connection between the contol Machine and the Managed Node ==> $sudo ansible all -m ping --private-key key.pem --user=ubuntu -e 'ansible_python_interpreter=/usr/bin/python3'
	