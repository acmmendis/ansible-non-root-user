
# Introduction

The Ansible role which consists many roles to deploy all necessary Service user accounts and their sudoers permissions.


# Which roles do what

- allusers.yml : All users
- ansible.yml : Ansible Service User
- cmdb.yml : CMDB Service User
- control-m.yml : Control Service User
- cyberark.yml : CyberArk Service User


# How to use

Pull the repo and run the playbook you want. Playbook the *allusers* to create all users and configurations. Use must specific individual playbooks to deploy the each role. You must provide Ansible Vault password to decrypt the credentiols of the user and inject. The master password you can find from keepass.

- All users :

  *ansible-playbook allusers.yml -i  ../ansible-dynamic-inventory/inventory/hcbi1weusubgenerigene001.yml -l linux -u svcansible --private-key ~/.ssh/svcansible_id_rsa --become --aks-vault-pass'*

- Just run one role:

  *ansible-playbook cmdb.yml -i  ../ansible-dynamic-inventory/inventory/hcbi1weusubgenerigene001.yml -l linux -u svcansible --private-key ~/.ssh/svcansible_id_rsa --become --aks-vault-pass'*

if you need to use password instead of private key, use below option and provide the password
  *ansible-playbook falcon.yml   -i 180.210.73.132, -u svcansible -Kk --extra-vars 'company=scbde env=pre'*

if you need to play on just one host
  *ansible-playbook allusers.yml -i 180.210.73.132,  -u svcansible  --private-key ~/.ssh/svcansible_id_rsa --become --aks-vault-pass*
