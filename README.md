Setup
=====
1. Install [VirtualBox](https://www.virtualbox.org/) (tested with 4.3.20)
1. Install [Vagrant](https://www.vagrantup.com/) (tested with 1.7.2)
1. Install [Ansible](http://www.ansible.com/home) (tested with 1.8.2)
1. Clone this repo
1. `gem install librarian-ansible`
1. `librarian-ansible install`
1. Review the roles to provision in ./Vagrant file (ansible.tags)
1. `vagrant up`
1. `vagrant provision` in case of any errors with provisioning
1. `vagrant reload`

Optional Setup
--------------
To make repeat provisioning faster, we can cache some of the downloaded packages by installing vagrant_cachier.

Install giveasia code
=====================
Use `ssh-add` to add your github key(s) to the authentication agent.
Then login to the box: `vagrant ssh`

In the box:

1. `cd workspace`
1. `git clone git@github.com:GIVESocialMovement/giviki2.git giveasia`
1. `cd giveasia`
1. `less README.md`
