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
                      inline: "sudo apt-get update && sudo apt-get -y upgrade && sudo apt-get -y install php7.4 php7.4-curl php7.4-mysql php7.4-mbstring php7.4-xml git mariadb-server"

  # create user and directories
  config.vm.provision "shell", 
                      inline: "id -u cloudlog &>/dev/null || sudo useradd -m -s /bin/bash cloudlog"
  config.vm.provision "shell", 
                      inline: " [[ -d /home/cloudlog/cloudlog-dist ]] && cd /home/cloudlog/cloudlog-dist; git pull || git clone https://github.com/magicbug/Cloudlog.git /home/cloudlog/cloudlog-dist"

  # set ownership
  config.vm.provision "shell", 
                      inline: "sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/application/config/ &&
                      sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/assets/qslcard/ &&
                      sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/backup/ &&
                      sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/updates/ &&
                      sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/uploads/ &&
                      sudo chown -R root:www-data /home/cloudlog/cloudlog-dist/images/eqsl_card_images/"
  # set ownership
  config.vm.provision "shell", 
                      inline: "sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/application/config/ &&
                      sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/assets/qslcard/&&
                      sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/backup/&&
                      sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/updates/&&
                      sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/uploads/&&
                      sudo chmod -R g+rw /home/cloudlog/cloudlog-dist/images/eqsl_card_images/"
  # create db
  config.vm.provision "shell", 
                      inline: 'sudo mysql -u root -p < /vagrant/create-db' 

end
