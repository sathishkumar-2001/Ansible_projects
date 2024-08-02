DAY - 06 -> create resources on aws using ansible and using ansible variables

collections - provides the modules to connect to the thrid part cloud provider apis liks aws , gcp , azure , etc
to use this collections firs tyou need to install the collections

for aws - ansible-galaxy collection install amazon.aws
you also need to install boto3 to connect to aws because ansible uses boto3 to connect to aws resources
pip install boto3

now we need to write a playbook for creation of ec2 instance in aws
