# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.network "private_network", type: "dhcp"
  config.vm.provision "shell", inline:  <<-SHELL
  apt-get update
  apt-get install -y bind9 dnsutils
SHELL

config.vm.define "tierra" do |tierra|
  
  tierra.vm.box = "debian/bookworm64"
  tierra.vm.network "private_network", ip: "192.168.57.103"
  tierra.vm.hostname = "tierra.sistema.test"

  tierra.vm.provision "shell", inline: <<-SHELL
  apt-get update
  apt-get install -y bind9 dnsutils

  cp -v /vagrant/named /etc/default
  cp -v /vagrant/named.conf.options /etc/bind
  systemctl restart named
  
  SHELL
end

config.vm.define "venus" do |venus|
  venus.vm.network "private_network", ip: "192.168.57.102"
end

end
