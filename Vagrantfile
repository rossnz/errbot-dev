# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "ubuntu/trusty64"

    config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.name = "errbot-dev"

    config.vm.synced_folder ".", "/vagrant"
end

    config.vm.provision "shell", inline: <<-SHELL
      sudo sed 's://archive.ubuntu.com://nz.archive.ubuntu.com:g' -i /etc/apt/sources.list
      sudo apt-get update
      sudo apt-get install python3-dev libssl-dev libffi-dev python3-pip git screen mc -y
      sudo pip3 -q install --upgrade pip
      sudo pip3 -q install err
      sudo pip3 -q install --upgrade six
      sudo pip3 -q install --upgrade setuptools
      sudo mkdir -p /home/vagrant/err-data /home/vagrant/err-plugins
      cp /vagrant/config.py /home/vagrant/.
      sudo chmod 655 /home/vagrant/config.py
      sudo chown -R vagrant /home/vagrant/*
      sudo apt-get autoremove -y
    SHELL
end
