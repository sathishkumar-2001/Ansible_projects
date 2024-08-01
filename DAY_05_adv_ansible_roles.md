DAY - 05 -> deep dive into ansible roles

we can use the roles available in the ansible galaxy page if the requirement is common 
many developers post their commonly used roles in this page we can use them if we want and make some modifications 


how we can use the roles in the ansible galaxy 
 1.) first login to ansible galaxy
 2.) select the role that you want to use
 3.) run this command - > ansible-galaxy role install <role name>
 4.) you can check the installed roles under /.ansible/roles/
 
to push your role to ansible galaxy
you need first to push the code to github
command to push -> ansible-galaxy import <github username> <nameofrep> --token <undercollectionssection>

