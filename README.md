# vbox-nobelbiz

Vagrantfile + Ansible Provisioning

Virtual Machine for Development of the NobelBiz Projects.

## Requirements

* [VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://vagrantup.com)
* [Nugrant](https://github.com/maoueh/nugrant)
* [Ansible](http://www.ansible.com)

## How To Install The Plugins

For vagrant 1.2+ run:
```bash
vagrant plugin install nugrant
```
## How To Build The Virtual Machine

Building the virtual machine is this easy:
```bash
host $ git clone https://github.com/josemrb/vbox-nobelbiz.git
host $ cd vbox-nobelbiz
host $ git submodule update --init --recursive
```
Copy the ```.vagrantuser.example``` file:
```bash
host $ cp .vagrantuser.example .vagrantuser
```
And edit the configuration to suit your needs.

## What's In The Box

- Git
- Utilities from https://github.com/Ansibles/utilities
- Redis 2.8.9
- MySQL -latest
- rbenv 0.4 with ruby 2.1.2
 
## First time setup
### MySQL
You can export the following environment variables:
- ```mysql_root_passwd``` to set the password for user: root (defaults to blank) 
- ```mysql_developer_passwd``` to set the password for user: developer (defaults to blank)

example:
```bash
host $ mysql_root_passwd=pass123 mysql_developer_passwd=pass321 vagrant up
```

## Recommended Workflow

The recommended workflow is:

* Edit files in the host computer
* Run within the virtual machine

## Virtual Machine Management

When done just log out with and suspend the virtual machine
```bash
host $ vagrant suspend
```
then, resume to hack again
```bash
host $ vagrant resume
```
Run
```bash
host $ vagrant halt
```
to shutdown the virtual machine, and
```bash
host $ vagrant up
```
to boot it again.

Or (for a shortcut) run
```bash
host $ vagrant reload
```
You can find out the state of a virtual machine anytime by invoking
```bash
host $ vagrant status
```
Finally, to completely wipe the virtual machine from the disk **destroying all its contents**:
```bash
host $ vagrant destroy # DANGER: all is gone
```
Please check the [Vagrant documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.

### Contributors
[josemrb](https://github.com/josemrb)  
[pablocrivella](https://github.com/pablocrivella)
