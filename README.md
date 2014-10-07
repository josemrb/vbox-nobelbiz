# vbox-nobelbiz

Vagrantfile + Ansible Provisioning

Virtual Machine for Development of the NobelBiz Projects.

## Requirements

* [VirtualBox](https://www.virtualbox.org)
* [Vagrant](http://vagrantup.com)
* [Ansible](http://www.ansible.com)
* [Nugrant Phttp://www.ansible.com/lugin](https://github.com/maoueh/nugrant)

## How To Install The Plugins

For vagrant 1.2+ run:

    vagrant plugin install nugrant

## How To Build The Virtual Machine

Building the virtual machine is this easy:

    host $ git clone https://github.com/josemrb/vbox-nobelbiz.git
    host $ cd vbox-nobelbiz
    host $ git submodule update --init --recursive

Rename the ```.vagrantuser.example``` file:

    host $ mv .vagrantuser.example .vagrantuser

And edit the configuration to suit your needs.

## What's In The Box

- Git
- Utilities from https://github.com/Ansibles/utilities
- Redis 2.8.9
- MySQL -latest
- rbenv 0.4 with ruby 2.1.2

## Recommended Workflow

The recommended workflow is:

* Edit files in the host computer
* Run within the virtual machine

## Virtual Machine Management

When done just log out with and suspend the virtual machine

    host $ vagrant suspend

then, resume to hack again

    host $ vagrant resume

Run

    host $ vagrant halt

to shutdown the virtual machine, and

    host $ vagrant up

to boot it again.

Or (for a shortcut) run

    host $ vagrant reaload

You can find out the state of a virtual machine anytime by invoking

    host $ vagrant status

Finally, to completely wipe the virtual machine from the disk **destroying all its contents**:

    host $ vagrant destroy # DANGER: all is gone

Please check the [Vagrant documentation](http://docs.vagrantup.com/v2/) for more information on Vagrant.
