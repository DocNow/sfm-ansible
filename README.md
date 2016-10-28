# sfm-ansible
Ansible playbooks for setting up Social Feed Manager

[![LICENSE](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](./LICENSE)


# Install Scripts for Social Feed Manager

The files are used to set up [Social Feed Manager](http://gwu-libraries.github.io/sfm-ui) on a target server. They can be used to install the application to a VM under Virtualbox or to a server running Ubuntu Trusty Tahr.

The `vagrant up` command is used to set up the server and deploy the application on the chosen platform.

## Installation

These scripts are intended to be run on a Unix-like system. They are tested to work on Mac OSX and Ubuntu Trusty-Tahr.

To use these scripts, [Vagrant](https://vagrantup.com) must already have been installed on the local system with the [Virtualbox](http://www.virtualbox.org/) provider working.

You will need version 1.6+ of [Vagrant](https://vagrantup.com) installed on the local system.

In addition [Ansible](https://ansible.com) at least 2.1+ will need to be installed. On Mac OS this can be installed via [Homebrew](https://brew.sh)
using the following command

```
brew install ansible
```

*On Ubuntu Trusty*

```
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible
```

Clone this repository on your local machine using git which is installed using the following command
```
brew install git
```

*On Ubuntu Trusty*

```
sudo apt-get install git
```

## Configuration


Make a copy of `ansible/group_vars/all_template` `ansible/example_hosts` and `ansible/example_ansible.cfg` file

```
cp ansible/group_vars/all_template ansible/group_vars/all
cp ansible/example_hosts ansible/hosts
cp ansible/example_ansible.cfg ansible/ansible.cfg
```

- Open the copied `ansible/group_vars/all` file and make the configuration changes needed.
- Open the copied `ansible/hosts` and enter the IP address of the target server.

## For Ansible Deployment

```
ansible-playbook ansible/site.yml -b
```

This assumes you have admin rights on the destination target server.

## Local VM

In the case of the `vagrant up` option, a VM will be brought up and configured in the current directory. The application is accessible on the local machine from a Web browser at the URI https://192.168.33.10 .

You can use vagrant ssh to log in to this VM when it is up. When logged out of the VM, vagrant halt can be used to shut down the VM. The command vagrant destroy will destroy it entirely, requiring another vagrant up to recreate it.

### Ansible

When using Ansible to provision directly, the playbook will be executed on the server whose IP address is given as IP. When the playbook finishes with no failures, the server is accessible at this URL:

```
http://<ip address>
```

### TO DO

- set up unattended playbook for AWS

### LICENSE
MIT
