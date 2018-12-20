# -*- mode: ruby -*-
# vi: set ft=ruby :
$Change = <<FILE_PERM
find ~/.prv/provisioning/ -type f |xargs dos2unix
FILE_PERM
Vagrant.configure("2") do |config|
  # Pull the vagrant box
  config.vm.box = "subham/devbox"
  # Set user under which provisioners will run
  config.ssh.username = "vagrant"
  config.ssh.password = "vagrant"
  #config.ssh.insert_key = false
  # Load up all possible files as a folder (to avoid erros on missing files)
  # Install ansible at remote host.
  config.vm.provision "file", source: "provisioning", destination: "~/.prv/"
  config.vm.provision "shell", privileged: false, inline: $Change
  config.vm.provision :shell, privileged: false, :inline => ". ~/.prv/provisioning/init.sh"
  config.vm.provision :shell, privileged: false, :inline => ". ~/.prv/provisioning/ansible.sh"
  config.vm.provider "virtualbox" do |vb|
  vb.name = "devbox"
  end
end
