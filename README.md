Setup
=====
1. Install [VirtualBox](https://www.virtualbox.org/)
1. Install [Vagrant](https://www.vagrantup.com/)
1. Clone this repo
1. `git submodule init && git submodule update`
1. `gem install librarian-ansible`
1. `librarian-ansible install`
1. Review the roles to provision in ./Vagrant file (ansible.tags)
1. `vagrant up`
1. `vagrant provision` in case of any errors with provisioning

Optional Setup
--------------
To make repeat provisioning faster, we can cache some of the downloaded packages by installing vagrant_cachier.

Install giveasia code
=====================
Use `ssh-add` to add your github key(s) to the authentication agent.
Then login to the box: `vagrant ssh`

In the box:
1. `cd workspace`
1. `git@github.com:GIVESocialMovement/giviki2.git giveasia`
1. `cd giveasia`
1. `less README.md`
