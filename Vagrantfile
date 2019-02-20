# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "generic/ubuntu1604"

  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.synced_folder "./puppet", "/etc/puppetlabs/code/environments/pbg"
  config.vm.synced_folder "./examples", "/examples"

  config.vm.provision "shell", path: "scripts/vagrant_provision.sh"

end