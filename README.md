# cloudlog-dist
A little vagrant project for cloudlog deployment automation. This project will create a debian stable vm and deploy cloudlog and all its dependencies in it. After that the user can use the installer to configure and start using the service. 

## Depencencies

* Vagrant from https://www.vagrantup.com
* Virtualbox from https://www.virtualbox.org

## Usage

After vagrant and virtualbox are installed and the repo has been cloned, you can create the vm by using: *vagrant up*

After the virtual machine is started you can view cloudlog under *http://localip/cloudlog*

If you want to stop the virtual machine use: *vagrant halt*


If you would like to delete the virtual machine and start again use: *vagrant destroy*

