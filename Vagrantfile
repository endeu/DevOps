# Vagrant.configure("2") do |config|
#     config.vm.define "DevOps" do |svr|
#       svr.vm.box = "centos/7"
#       svr.vm.provider "virtualbox" do |vb|
#         vb.name = "DevOps1"
#         vb.memory = 512
#         vb.cpus = 1
#       end
#     end

#     config.vm.define "DevOps2" do |svr2|
#       svr2.vm.box = "ubuntu/focal64"
#       svr2.vm.provider "virtualbox" do |vb|
#         vb.name = "DevOps2"
#         vb.memory = 1024
#         vb.cpus = 1
#     end
#   end
# end





# -*- mode: ruby -*-
# vi:set ft=ruby sw=2 ts=2 sts=2:

#$ = <<-
#sequencia de comandos
#para executar durante o provisionamento
#

NUM_NODE = 2
IMAGE_BOX = "ubuntu/bionic64"
NODE_NAME = "svr"
NODE_MEM = 1024
NODE_CPU = 1

IP_NW = "192.168.56." #Ip virtualbox, somente as máquinas do vitualbox irão se conectar
NODE_IP_START = 10

Vagrant.configure("2") do |config|
  config.vm.box = "#{IMAGE_BOX}"
  config.vm.box_check_update = false

  # Provision Nodes).each do |i|
  (1..NUM_NODE).each do |i|
    config.vm.define "#{NODE_NAME}0#{i}" do |node|
        node.vm.provider "virtualbox" do |vb|
            vb.name = "#{NODE_NAME}#{i}"
            vb.memory = "#{NODE_MEM}"
            vb.cpus = "#{NODE_CPU}"
        end
        node.vm.hostname = "#{NODE_NAME}#{i}"
        node.vm.network :private_network, ip: IP_NW + "#{NODE_IP_START + i}"
        #node.vm.network "public_network", bridge: "wlp0s20f3"
        node.vm.network "forwarded_port", guest: 22, host: "#{2200 + i}"
        #node.vm.provision "shell", inline: $
        #node.vm.provision "setup-hosts", :type => "shell", :path => "ubuntu/vagrant/setup-hosts.sh" do |s|
    end
        
  end
end
