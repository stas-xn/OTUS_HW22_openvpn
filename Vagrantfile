# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"


  config.vm.provider "virtualbox" do |v|
	  v.memory = 256
  end

  config.vm.define "openvpn-server" do |ns01|
    ns01.vm.network "private_network", ip: "192.168.50.10", virtualbox__intnet: "dns"
    ns01.vm.hostname = "openvpn-server"
  end

  config.vm.define "openvpn-client" do |ns02|
    ns02.vm.network "private_network", ip: "192.168.50.11", virtualbox__intnet: "dns"
    ns02.vm.hostname = "openvpn-client"
  end


end
