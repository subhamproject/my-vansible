# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  # Pull the vagrant box
  config.vm.box = "ubuntu/xenial64"
  # Set user under which provisioners will run
  config.ssh.username = "vagrant"
  config.ssh.password = "vagrant"
  # Load up all possible files as a folder (to avoid erros on missing files)
  # Install ansible at remote host.
  config.vm.provision "file", source: "provisioning", destination: "~/."
  config.vm.provision :shell, privileged: false, :inline => ". ~/provisioning/init.sh"
  config.vm.provision :shell, privileged: false, :inline => ". ~/provisioning/ansible.sh"
  config.vm.provider "virtualbox" do |vb|
  vb.name = "rcx-devbox"
  end
end
