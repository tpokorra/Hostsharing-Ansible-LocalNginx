Hostsharing-Ansible-LocalNginx
==============================
This Ansible playbook will install a local Nginx on a server from www.hostsharing.net.
It requires an additional daemon, and an assigned port number.

To use these modules we have to create a file named ".hsadmin.properties" in the home directory of the package admins. In it we have to insert the packagename and password of the package admin. 

Example:

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=insertpkgadminpasswordhere

This file should be protected, else it would be world readable:

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine:

    $ git clone https://github.com/tpokorra/Hostsharing-Ansible-LocalNginx.git

Then we change the working directory:

    $ cd Hostsharing-Ansible-LocalNginx

All needed parameters can be set in the inventory file now. Change xyz00 to the name of your package admin. Set the name of a domain, a new user and a password. We can edit the inventory file with:

    $ vim inventory
    
The option -i can be used to read this inventory file instead of the /etc/ansible/hosts file. If we want to login with an SSH-Key instead of an SSH-Password, we have to remove the -k option from the following string. We run:

    $ ansible-playbook -i inventory playbook-localnginx.yml -k

Now we can reach our site via:

    https://demo.example.org

--- Open Source Hosting ---
 https://www.hostsharing.net
