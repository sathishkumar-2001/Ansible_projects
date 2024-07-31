DAY - 2 : 
controll node (master) managed node (worker)
passwordless authentication - helps us not to provide the authentication on each time in the managed nodes , this is basically one time activity
we can provide the pem file or password of the nodes

How to setup Passwordless Authentication
EC2 Instances
Using Public Key
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
ssh-copy-id: This is the command used to copy your public key to a remote machine.
-f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
"-o IdentityFile ": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
ubuntu@: This is the username (ubuntu) and the IP address of the remote server you want to access.

Using Password
Go to the file /etc/ssh/sshd_config.d/60-cloudimg-settings.conf
Update PasswordAuthentication yes
Restart SSH -> sudo systemctl restart ssh

for providing the details of the target nodes like public ip username , password  we use inventory file -> inventory.ini
note : we also write the inventory file in yaml format also 
we can create inventory file at any location but if you don't want to provide the inventory location each time it will take the file default at /etc/ansible/hosts here create the inventory file

there are two ways of providing the instructions to ansible using adhoc commands and playbooks in yaml format
for smaller tasks we can use adhoc commands for multi tasks we can use playbooks

Basic adhoc commands

ansible -i inventory.ini -m ping all
ansible -i inventory.ini -m shell -a "apt install sshpass " all

suppose if your having 10 app servers and 4 db servers now if you want install some apk in only app server is it possible ?
yes it is possible by grouping in the inventory file like [appservers] [dbservers]
so we can group the managed nodes
  
