# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"


  config.vm.network "forwarded_port", guest: 8080, host: 8080

  config.vm.synced_folder "/Users/girishpandit/Documents/GitHub/play-otto-sample/target", "/vagrant"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-add-repository ppa:webupd8team/java
    sudo apt-get update
    echo debconf shared/accepted-oracle-license-v1-1 select true | sudo debconf-set-selections
    echo debconf shared/accepted-oracle-license-v1-1 seen true | sudo debconf-set-selections
    sudo apt-get install -y oracle-java8-installer oracle-java8-set-default unzip
    unzip /vagrant/universal/play-otto-sample-1.0-SNAPSHOT.zip -d /opt/
    cd /opt/play-otto-sample-1.0-SNAPSHOT/
    nohup ./bin/play-otto-sample -Dhttp.port=8080 &
  SHELL
end
