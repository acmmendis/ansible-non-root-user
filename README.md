# Introduction

The Ansible roles create system user accounts. There are two roles:
1. `root_user`: Creates a root user account.
2. `non_root_user`: Creates a non-root user account and requires a sudoers file to be provided as a variable.

The play creates a static password for the user, which will be output at the end of the play.

# How to use

1. Pull the repository and change the *roles/non_root_user/vars/main.yml* or *roles/root_user/vars/main.yml* as per your new user's information. Add required permissions in *roles/non_root_user/files/sudoers_user* if using the non-root user role.

2. Run the main playbook which will give you the temporary password for the respective user.

## Example Commands

### For creating a root user

```sh
ansible-playbook root.yml -i inventory.yml -u svcansible --private-key ~/.ssh/svcansible_id_rsa --become -e 'systemuser=rootuser comments="This is a root user"'
```

### For creating a non-root user

```sh
ansible-playbook non-root.yml -i inventory.yml -u svcansible --private-key ~/.ssh/svcansible_id_rsa --become -e 'systemuser=usrespro001 comments="This is a non=root user with sudoers access" sudoers_user_file=/path/to/sudoers_user_file'
```

