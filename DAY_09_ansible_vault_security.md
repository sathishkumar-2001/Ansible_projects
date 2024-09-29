DAY - 09 -> Ansible vault for security

vault - is used to secure any kind of sensitive informations like password , tokens , usernames, templates to encrypt with ansible playbook

it is very important to secure the sensitive informations to follow the devsecops 
command - ansible-vault 

encrypt process in vault :
  * create a new file under group_vars 
  * create a yaml file and add the sensitive informations like for aws access_key and secret_key
  * ansible-vault create <nameoffilewheresecrtestoredyaml> 
  * it will prompt for new password
  * thats it it will encrypt the secrets without password no one can access it

arguments used for ansible-vault command
     create - create new vault encrypted file
	 decrypt - decrypt vault encrypted file
	 edit - edit vault encrypted file
	 view - view vault encrypted file
	 encrypt - encrypt yaml file
	 encrypt_string - encrypt a string
	 rekey - Re-key a vault encrypted file

we can also used openssl for passwords -> openssl rand -base64 2048

ansible-vault create aws_cred.ymal --vault-password-file vault.pass

