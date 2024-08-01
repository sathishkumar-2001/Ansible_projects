DAY - 04 -> understanding ansible roles

suppose if your having 2000 lines of playbook it creates a problem of readability 
Role - plays a major role of dividing the entire playbook into different yaml files 

we can create role using ansible-galaxy
For most complicated tasks we can use roles

Advantages of roles -> readability , modularity , we can upload at github or ansible-galaxy and share across organization

creation of role using ansible-galaxy
    ansible-galaxy role init test 
	it will create the test directory 
	inside test directory we can see , 
	README.md  defaults  handlers  meta  tasks  tests  vars
	
	handlers consists of some notify required by the task we add them under handlers
	
	to run the role command is -> ansible-playbook -i inventory.ini first-playbook.yaml
	
ansible is idempotent in nature means it won't execute the task again if it is already there

