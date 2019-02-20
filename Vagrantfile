# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu1604"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./puppet", "/etc/puppetlabs/code/environments/pbg"
  config.vm.synced_folder "./examples", "/examples"

  ## This folder was added by me
  #config.vm.synced_folder "/home/jaime/workspace/puppet/puppet-bg3", "/etc/puppetlabs/code/environments/production"

  config.vm.provision "shell", path: "scripts/vagrant_provision.sh"

  config.vm.provision "shell", :inline => <<-SHELL
  cd /etc/puppetlabs/code/environments
  sudo mv production production.sample
  sudo git clone https://github.com/jinostrozam/puppet-bg3.git production
  cd /etc/puppetlabs/code/environments/production
  sudo git pull
  sudo puppet apply manifests/
  SHELL

end