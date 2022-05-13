# -*- mode: ruby -*-"
# vi: set ft=ruby :

box_type= "debian/bullseye64"

Vagrant.configure("2") do |config|
  config.vm.box = "#{box_type}"
  config.vm.network "public_network", bridge: 'wlp0s20f3'
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 1
  end

  
  # ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  # Add packages
  # ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
  config.vm.provision "shell", 
                      inline: "sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install php7.4 php7.4-curl php7.4-mysql php7.4-mbstring php7.4-xml git"
  # install mariadb
  config.vm.provision "shell", 
                      inline: "sudo /bin/bash /vagrant/mariadb-install  "
  

  # create cloudlog dir and clone cloudlog
  config.vm.provision "shell", 
                      inline: "sudo /bin/bash /vagrant/docker/clone-cloudlog"

  # set ownership
  config.vm.provision "shell", 
                      inline: "sudo /bin/bash /vagrant/docker/set-ownership"
  # set permissions
  config.vm.provision "shell", 
                      inline: "sudo /bin/bash /vagrant/docker/set-permissions"
  # create db
  config.vm.provision "shell", 
                      inline: 'sudo mysql -u root -ps3kr1t < /vagrant/docker/create-db' 

end
