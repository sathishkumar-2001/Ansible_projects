DAY - 06 -> create resources on aws using ansible and using ansible variables

collections - provides the modules to connect to the thrid part cloud provider apis liks aws , gcp , azure , etc
to use this collections firs tyou need to install the collections

for aws - ansible-galaxy collection install amazon.aws
you also need to install boto3 to connect to aws because ansible uses boto3 to connect to aws resources
pip install boto3

now we need to write a playbook for creation of ec2 instance in aws

--- 
- hosts: localhost
  connection: local
  tasks:
  - name: start an instance with a public IP address
    amazon.aws.ec2_instance:
      name: "ansible-instance"
      # key_name: "prod-ssh-key"
      # vpc_subnet_id: subnet-013744e41e8088axx
      instance_type: t2.micro
      security_group: default
      region: us-east-1
      aws_access_key: "{{ec2_access_key}}"  # From vault as defined
      aws_secret_key: "{{ec2_secret_key}}"  # From vault as defined      
      network:
        assign_public_ip: true
      image_id: ami-04b70fa74e45c3917
      tags:
        Environment: Testing
		
get the aws access_key and secret_key from aws website

while running the playbook you need to provide the password for the vault
ansible-playbook -i inventory.int <name.ymal> --vault-password-file <name.pass>

collection always run on controll node
each collections have pre requisite based on public cloud providers

in any programming it is best to not hardcord any values

in ansible playbook yaml file we will be using jinja2 template
within two curly braces {{ }} we will provide the variable name

there are totally 22 ways declaring variable in ansible

varibles priority
default/main.yaml < vars/main.yaml < -e "type=t2.micro" (extravars has the highest precedence)

