DAY - 03 -> writing Ansible Playbooks

playbooks are written in yaml format 
playbooks is a list of play
play contains some tasks
inside tasks we will be using modules to run our commands

simple playbook to create directory and create file inside it 
command to run the playbook -> ansible-playbook -i inventory.ini first-playbook.yaml
---
- name: Create directory and file
  hosts: all
  become: yes
  tasks:
    - name: Create directory "test"
      file:
        path: /path/to/test
        state: directory
        mode: '0755'

    - name: Create a file named "test.txt" inside the "test" directory
      copy:
        dest: /path/to/test/test.txt
        content: "This is a test file."
        mode: '0644'


Explanation
hosts: all: This indicates that the playbook will be run on all hosts specified in the inventory file.
become: yes: This allows the playbook to run tasks as a privileged user (e.g., root).
tasks: This section contains the tasks to be executed.

output of the above playbook 

PLAY [Create directory and file] ********************************************************

TASK [Gathering Facts] ******************************************************************
ok: [azureuser@20.244.90.173]

TASK [Create directory "test"] **********************************************************
changed: [azureuser@20.244.90.173]

TASK [Create a file named "test.txt" inside the "test" directory] ***********************
changed: [azureuser@20.244.90.173]

PLAY RECAP ******************************************************************************
azureuser@20.244.90.173    : ok=3    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   


we can also use build in ansible modules for tasks
link -> https://docs.ansible.com/ansible/latest/collections/ansible/builtin/
