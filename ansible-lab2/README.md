# Ansible Lab 2 - Ad HOC tasks and Modules


1. Use APT module to install services
2. Use service module to manage services
3. Use ansible to reboot webstack

### Install Services using APT module
https://docs.ansible.com/ansible/latest/modules/apt_module.html
``` shell
# run apt update on all servers
ansible all -i hosts --become -m apt -a "update_cache=yes"
# run apt install apache2 on webservers 
ansible webservers -i hosts --become -m apt -a "name=apache2 state=present"
# run apt install mysql-server on database
ansible database -i hosts --become -m apt -a "name=mysql-server state=present"
```

### Restart Services using Service module
https://docs.ansible.com/ansible/latest/modules/service_module.html
``` shell
ansible database -i hosts -m service -a "name=mysql state=started"
ansible database --become -i hosts -m service -a "name=mysql state=restarted"
 ```

### Use Ansible to reboot the webstack, will need to stop and restart the servers manually
``` shell
ansible webstack -i hosts --become -a "reboot --reboot"
 ```
