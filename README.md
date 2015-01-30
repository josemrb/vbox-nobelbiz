# vboxes
Vagrant + VirtualBox + Ansible.  
Guest machines for development.

## Requirements
- [VirtualBox 4.2.x](https://www.virtualbox.org)
- [Vagrant 1.7.x](https://vagrantup.com)
  - [Nugrant](https://github.com/maoueh/nugrant)
  - [vagrant-hostmanager](https://github.com/smdahlen/vagrant-hostmanager)
- [Ansible 1.8.x](http://www.ansible.com)

### How to install the Vagrant plugins?
Inside a shell run:
```sh
$ vagrant plugin install nugrant
$ vagrant plugin install vagrant-hostmanager
```

## Boxes
### ruby.dev
- git
- cron
- Node.js
- Redis
- MySQL
- Ruby

#### How to build the guest machine
First, clone the repository.
```sh
$ git clone https://github.com/josemrb/vboxes.git
$ cd vboxes
```

Then, create an user specific configuration file, you should copy the `.vagrantuser.example` file and use it as the base.
```sh
$ cp .vagrantuser.example .vagrantuser
```

At last, execute Vagrant to create and configure the guest machine.
```sh
$ vagrant up
```

If everything goes well, now you can SSH into the guest machine to have access to a shell.
```sh
$ vagrant ssh
```

Please check the [documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.

## Provisioning Framework
### Default roles
The following roles are installed by default.

#### [ANXS/timezone](https://github.com/ANXS/timezone)
Role for setting/updating the timezone.
##### Variables
To change the default value edit the `.vagrantuser` file and update the item in the `vboxes.[name].ansible.vars` hash.
```yaml
timezone_zone: UTC          # valid tz database string
```

#### [ANXS/build-essential](https://github.com/ANXS/build-essential)
Role which installs packages required for compiling C software from source.

#### [ANXS/git](https://github.com/ANXS/git)
Role which installs the git package.

#### [ANXS/cron](https://github.com/ANXS/cron)
Role which installs the cron package and starts the crond service.

#### [ANXS/utilities](https://github.com/ANXS/utilities)
Role which installs a selection of useful, must-have utilities.

### Optional Roles
#### [nodesource.node](https://github.com/nodesource/ansible-nodejs-role)
Role which adds the NodeSource APT repository and installs the nodejs package.  
To enable edit the .vagrantuser file and add the item to the `vboxes.[name].ansible.roles` array.
```yaml
- nodejs
```

#### [DavidWittman.redis](https://github.com/nodesource/ansible-nodejs-role)
Role which downloads and builds Redis.  
To enable edit the .vagrantuser file and add the item to the `vboxes.[name].ansible.roles` array.
```yaml
- redis
```
##### Variables
To change the default value edit the `.vagrantuser` file and update the item in the `vboxes.[name].ansible.vars` hash.
```yaml
redis_version: 2.8.8
```

#### [ANXS/mysql](https://github.com/ANXS/mysql)
Role which installs and configure an MySQL instance.  
To enable edit the .vagrantuser file and add the item to the `vboxes.[name].ansible.roles` array.
```yaml
- mysql
```
##### Variables
To change the default value edit the `.vagrantuser` file and update the item in the `vboxes.[name].ansible.vars` hash.
```yaml
mysql_root_password: 1234qwer
mysql_users:
  - name: developer
    pass: 
    priv: "*.*:ALL"
    host: "%"
```

#### [pablocrivella/ansible-role-rbenv](https://github.com/pablocrivella/ansible-role-rbenv)
Role which installs rbenv with selected plugins and builds Ruby from source.  
To enable edit the .vagrantuser file and add the item to the `vboxes.[name].ansible.roles` array.
```yaml
- rbenv
```
##### Variables
To change the default value edit the `.vagrantuser` file and update the item in the `vboxes.[name].ansible.vars` hash.
```yaml
ruby_version: 2.2.0
ruby_gems_default:
  - bundler
```

### Contributors
[josemrb](https://github.com/josemrb)  
[pablocrivella](https://github.com/pablocrivella)
