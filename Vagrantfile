# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    nodes = {
        'seafahrer' => { :ip  => '10.30.30.70', :memory => 512, :cpus => 2 },
    }

    nodes.each do |node_name, node_opts|
        config.vm.define node_name do |node_config|
            #node_config.vm.hostname = "#{node_name}"
            node_config.vm.box = "ubuntu-15.04-amd64"
            node_config.vm.box_url = "https://github.com/kraksoft/vagrant-box-ubuntu/releases/download/15.04/ubuntu-15.04-amd64.box"

            node_config.vm.network :private_network, ip: node_opts[:ip]

            node_config.vm.provider "virtualbox" do |v|
                v.gui = false
                unless node_opts[:memory].nil?
                    modifyvm_args = ['modifyvm', :id]
                    modifyvm_args << '--memory' << node_opts[:memory].to_s
                    v.customize(modifyvm_args)
                end
            end
        end
    end
end

