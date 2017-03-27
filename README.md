# Instructions

This Ansible Playbook creates ssh key, security group, applies security rules for port 22 and 80 and creates the given number of ec-instances. 

To get started, one will need a AWS account and security credentials 


1. Go to: http://aws.amazon.com/
2. Sign Up & create a new account (they "MAY" give you the option for 1 year trial or similar. Requires payment information)
3. Go to your AWS account overview
4. Account menu in the upper-right (has your name on it)
5. Sub-menu: Security Credentials



After you have your account setup and retrieved security credentials, you can run the playbook 

1. Install Ansible 

	Linux 

		sudo easy_install pip
		sudo pip install ansible

	Unix

		brew install ansible


	It is suggested to run Ansible master server in Linux or Unix machine. Installing and running Ansible master in Windows is fairly complex. One can follow this tutorial to do so. 

		https://www.jeffgeerling.com/blog/running-ansible-within-windows


	Test Ansible installation. In command line, 

  		ansible --version 
  
	This should produce output similar as follows  


		ansible 2.1.1.0
		config file =
		configured module search path = Default w/o overrides
  

2. Update the keys as per your account information(required)

	    aws_access_key: <your aws access key> 
   		aws_secret_key: <your aws security key> 

	Update the following variables as per needed(optional) 
		
		region: us-east-1
		group_name: ec2_server_group
		instance_type: t2.micro 
		image_id: ami-b63769a1
    	number_of_instances: 1
		

3. Run the playbook, from command line, 

		git clone https://github.com/mohiuddinopu/aws_api_ansible.git
		cd aws_api_ansible
		ansible-playbook ansible_deploy_ec2-instances.yml


4. Check instances 

		a. Go to: http://aws.amazon.com/
		b. Sign in
		c. Navigate to EC2 > EC2 Dashboard > Running Instances 
		d. Check for newly created instances 



NOTE: Terminate your instances once done with your usage. You will get charged if the instances are not terminated. 