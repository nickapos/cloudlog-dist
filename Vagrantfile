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

  # create user and directories
  config.vm.provision "shell", 
                      inline: "id -u cloudlog &>/dev/null || sudo useradd -m -s /bin/bash cloudlog"
  config.vm.provision "shell", 
                      inline: " git clone https://github.com/magicbug/Cloudlog.git  /home/cloudlog/cloudlog-dist"

  # set permissions
  config.vm.provision "shell", 
                      inline: "sudo chown -R root:www-data /var/www/html/application/config/\
                      sudo chown -R root:www-data /var/www/html/assets/qslcard/\
                      sudo chown -R root:www-data /var/www/html/backup/\
                      sudo chown -R root:www-data /var/www/html/updates/\
                      sudo chown -R root:www-data /var/www/html/uploads/\
                      sudo chown -R root:www-data /var/www/html/images/eqsl_card_images/" 

end
