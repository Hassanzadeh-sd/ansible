# ansible_playbooks

these are the playbooks used for configuration management and multi-machine deployment system.

## Install Ansible

#### Ubuntu

```bash
sudo apt update
sudo apt upgrade -y
sudo reboot
sudo apt install -y software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt update
sudo apt install -y ansible
ansible --version
```

#### Setup SSH keys and share it among managed nodes

```bash
ssh-keygen
ssh-copy-id node1.example.com
```

## Run Playbooks

first of all you have to set server ssh's pass word in group vars and host vars with `ansible_sudo_pass` env
example :
group_vars/all.yaml

```bash
ansible_sudo_pass: 'pass'
```

or run playbook first run :

```bash
ansible-playbook set_sudoer.yaml -b -K
```

and install vim and docker and nginx with this command :

```bash
ansible-playbook -i inventory/hosts.yaml playbooks/initial_tasks.yaml
```
