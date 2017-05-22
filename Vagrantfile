# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.vm.network "forwarded_port", guest: 3000, host: 3000 # rails
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus   = 1
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'provisioning/playbook.yml'
    ansible.verbose = 'v'
    ansible.groups = {
      'workstation' => ['default']
    }

    ansible.extra_vars = {
      rvm1_rubies: ['ruby-2.3.1', 'ruby-2.4.1'],
      rvm1_default_ruby_version: '2.3.1',
      postgresql_version: '9.6.3',
      postgresql_users: [
        name: 'vagrant',
        role_attr_flags: 'createdb'
      ],
      nodejs_version: '7.10',
      verbose: true,
    }

    ansible.tags = [
      'packages',
      'locale',
      'workstation',
      'ruby',
      'gems',
      'postgresql',
      'nodejs',
    ]
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.auto_detect = false
    config.cache.scope = :box
    config.cache.enable :apt
  end
end
