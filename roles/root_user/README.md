### Ansible playbook for deploy servicenow CMDB user

Service now team requested to create a user in all the Linux vms in order to build an inventoy with service maps.

This playbook is for create the required user with specific access. The least privilage granted from a dedicated sudoers file.

#### 1.1. How to use

- The playbook should be executed from the ansible master nodes in each subscriptions.
- Inventory file can be found in the Ïnventoy" for for each subscriptions.
- There are groups for rhel,deb and winodws.
- Use the service user "svcansible" for deployment
- Use "ansible vault encryption" secret to decrypt the var.yml

`ansible-playbook service_user_cmbd.yml -i inventory/hcbi1weusubgenerigene001.yml -l rhel -u svcansible -Kk --ask-vault-pass`
