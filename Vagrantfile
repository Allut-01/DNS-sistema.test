# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"



config.vm.define "tierra" do |tierra|
  
  tierra.vm.box = "debian/bookworm64"
  tierra.vm.network "private_network", ip: "192.168.57.103" 
  tierra.vm.hostname = "tierra.sistema.test"

  tierra.vm.provision "shell", inline: <<-SHELL

  apt-get update
  apt-get install -y bind9 dnsutils

  cp -v /vagrant/named /etc/default
  cp -v /vagrant/named.conf.options /etc/bind
  cp -v /vagrant/named.conf.local /etc/bind
  cp -v /vagrant/db.sistema.test /etc/bind
  cp -v /vagrant/db.192 /etc/bind

  systemctl restart named

  SHELL
  end

config.vm.define "venus" do |venus|
  venus.vm.box = "debian/bookworm64"
    venus.vm.network "private_network", ip: "192.168.57.102"
    venus.vm.hostname = "venus.sistema.test"

    venus.vm.provision "shell", inline: <<-SHELL

    apt-get update
    apt-get install -y bind9 dnsutils
  
    cp -v /vagrant/named.conf.options /etc/bind/
    cp -v /vagrant/named.conf.local /etc/bind/

    SHELL

  
  end

end

