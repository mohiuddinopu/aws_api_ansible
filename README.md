# Instructions

This Ansible Playbook creates ssh key, security group, applies security rules for port 22 and 80 and creates the given number of ec2-instances. 

To get started, one will need a AWS account and security credentials 


1. Go to: http://aws.amazon.com/
2. Sign Up & create a new account (they "MAY" give you the option for 1 year trial or similar. Requires payment information)
3. Go to your AWS account overview
4. Account menu in the upper-right (has your name on it)
5. Sub-menu: Security Credentials



After you have your account setup and retrieved security credentials, you can run the playbook 

1. Install Ansible and Git

	Linux 

		yum install git-all
		sudo easy_install pip
		sudo pip install ansible

	Unix

		brew install ansible git-all
		
	To install git on Mac, follow this link
		https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
		


	It is suggested to run Ansible master server in Linux or Unix machine. Installing and running Ansible master in Windows is fairly complex. One can follow this tutorial to do so. 

		https://www.jeffgeerling.com/blog/running-ansible-within-windows


	Test Ansible installation. In command line, 

  		ansible --version 
  
	This should produce output similar as follows  


		ansible 2.1.1.0
		config file =
		configured module search path = Default w/o overrides
  

3. Download git repository 

		git clone https://github.com/mohiuddinopu/aws_api_ansible.git

2. Update the keys in "..roles/<playbook>/vars/main.yml" as per your account information(required)

       		aws_access_key: <your aws access key> 
		aws_secret_key: <your aws security key> 

	Update the following variables as per needed(optional) 
		
		region: us-east-1
		group_name: ec2_server_group
		instance_type: t2.micro 
		image_id: ami-b63769a1
    	number_of_instances: 1
		



4. Check EC2 Instances 

		a. Go to: http://aws.amazon.com/
		b. Sign in
		c. Navigate to EC2 > EC2 Dashboard > Running Instances 
		d. Check for newly created instances 

5. Run playbooks
		
		ansible-playbook create_ec2_instances.yml
	  	ansible-playbook create_cloudera_director_instance.yml
  		ansible-playbook create_wordpress_instance.yml
  
6. Accessing instance

		a. To access the ec2 instance http://aws.amazon.com/
		b. Navigate to EC2 > EC2 Dashboard > Running Instances 
		c. Select the instance you want to log in, click 'Connect'
		d. SSH keys are stored in 'keys' directory in your ansible repo path

7. Accessing Cloudera Director(Allow at least 5 minutes of time for the Director process to be up and running)

		a. To access the ec2 instance http://aws.amazon.com/
		b. Navigate to EC2 > EC2 Dashboard > Running Instances 
		c. Select the Cloudera Director instance, and look for the Public IPV4
		d. In a browser, navigate to <Public IP>:7189

8. Accessing WordPress

		a. To access the ec2 instance http://aws.amazon.com/
		b. Navigate to EC2 > EC2 Dashboard > Running Instances 
		c. Select the Wordpress instance, and look for the Public IPV4
		d. In a browser, navigate to <Public IP>
		
9. Accessing WordPress Admin UI

		a. To access the ec2 instance http://aws.amazon.com/
		b. Navigate to EC2 > EC2 Dashboard > Running Instances
		c. Select WordPress instance, and click the Actions button. In the drop down menu, select Instance Setting, and choose Get System Log
		d. In the system log window, scroll through to the bottom to find the password that's surrounded by hash marks
		
<img width="832" alt="wordpress_admin_password" src="https://cloud.githubusercontent.com/assets/14286463/24945912/18c8b096-1f2f-11e7-851e-b11fed5ff1cd.png">


NOTE: Terminate your instances once done with your usage. You will get charged if the instances are not terminated. 
