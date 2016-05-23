# -*- mode: ruby -*-
# vi: set ft=ruby :

#rtr_xr_cfg_file_remote = "/home/vagrant/xr_config" 

Vagrant.configure(2) do |config|

  config.vm.provision "shell", inline: "echo Hello User"

  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/trusty64"
    ubuntu.vm.network :private_network, virtualbox__intnet: "link1", ip: "10.1.1.10"
    ubuntu.vm.provision :shell, path: "ubuntu.sh", privileged: false
	  ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
  	#ubuntu.vm.provision "shell", inline: "echo #{ssh_pub_key}"
  end

  config.vm.define "xr" do |xr|
    xr.vm.box = "xrv64"
    #xr.vm.provision 'shell', inline: "echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys", privileged: false
    xr.vm.network :private_network, virtualbox__intnet: "link1", ip: "10.1.1.20"
  end
   
end
