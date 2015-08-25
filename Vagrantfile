# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "forwarded_port", guest: 1080, host: 1080
  config.ssh.forward_agent = true

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus   = 2
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = 'provisioning/playbook.yml'
    ansible.verbose = 'v'
    ansible.groups = {
      'workstation' => ['default']
    }

    ansible.extra_vars = {
      ruby_versions: ['2.0.0', '2.2.2'],
      ruby_default: '2.2.2',
      chromedriver_version: '2.18',
    }

    ansible.tags = [
      'update-packages',
      'locale',
      'java',
      'ruby',
      'gems',
      'nodejs',
      'workstation',
      'headless',
      'mongodb',
      'packages',
      'chrome',
      'chromedriver',
    ]
  end

  if Vagrant.has_plugin?("vagrant-cachier")
    config.cache.auto_detect = false
    config.cache.scope = :box
    config.cache.enable :apt
  end
end
