
# Introduction

The Ansible role which create a single system user accounts without any priviladge. The play create a static passowd for this user. 
The password will output at the play end.


# How to use

Pull the repo and chnage the *roles/non_root_user/var/main.yml* as per your new users information. Add required permissions in *roles/non_root_user/files/sudoers_user*

Run the main playbook which will give you the temporary password for the respected user.

For mass creation based on inventory

  *ansible-playbook non-root.yml -i ../ansible-dynamic-inventory/inventory/hcbi1weusubgenerigene001.yml -u svcansible --private-key ~/.ssh/svcansible_id_rsa --become -e 'systemuser=usrespro001 comments="This is a test user"'*

if you need to use password instead of private key, use below option and provide the password
  *ansible-playbook root.yml   -i 180.210.73.132, -u svcansible -Kk'*

if you need to play on just one host
  *ansible-playbook root.yml -i 180.210.73.132,  -u svcansible  --private-key ~/.ssh/svcansible_id_rsa --become -e 'systemuser=usrespro001 comments="This is a test user"'*
