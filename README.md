# User Creation

This project configures two Virtual Machines using Vagrant and VirtualBox: app1, db1 and creates two groups: admin, developer & users with Ansible playbook based on entries present in ```users.yml```. 

## Pre-requisites

1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Downloads).
2. Download and install [Vagrant](http://www.vagrantup.com/downloads.html).
3. [Mac/Linux only] Install [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html).
4. Update ```users.yml``` with public keys added in ```/keys``` that can be used for testing user-access.

## Implementation

1. In Terminal, cd to the directory containing the Vagrantfile & Ansible playbook. Run the command given below to start the virtual machines.
```bash
vagrant up
```

2. To run the Ansible playbook on the virtual machines,
```bash
ansible-playbook user_playbook.yml -i inventory
```

## Testing
1. Login to any(app1/db1) virtualbox with ```vagrant``` user and check the list of users & groups.
```bash
vagrant ssh app1
grep '^<group_name>:' /etc/group
```

2. Check the permissions, restrictions by logging in as the created user.
```bash
ssh -i '<user_private_key>' '<username>'@'<app/db-hostname>'
```

## License
[MIT](https://choosealicense.com/licenses/mit/)