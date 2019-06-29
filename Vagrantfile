# -*- mode: ruby -*-
# vi: set ft=ruby :

servers = [
    {
        :name => "k8s-head",
        :type => "master",
        :box => "ubuntu/bionic64",
        :box_version => "20190627.1.0",
        :eth1 => "192.168.0.60",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "k8s-node-1",
        :type => "node",
        :box => "ubuntu/bionic64",
        :box_version => "20190627.1.0",
        :eth1 => "192.168.0.61",
        :mem => "2048",
        :cpu => "2"
    },
    {
        :name => "k8s-node-2",
        :type => "node",
        :box => "ubuntu/bionic64",
        :box_version => "20190627.1.0",
        :eth1 => "192.168.0.62",
        :mem => "2048",
        :cpu => "2"
    }
]

Vagrant.configure("2") do |config|

    servers.each do |opts|
        config.vm.define opts[:name] do |config|

            config.vm.box = opts[:box]
            config.vm.box_version = opts[:box_version]
            config.vm.hostname = opts[:name]
            config.vm.network :public_network, ip: opts[:eth1], bridge: "wlp3s0"

            config.vm.provider "virtualbox" do |v|

                v.name = opts[:name]
            	 v.customize ["modifyvm", :id, "--groups", "/Kubernetes Lab"]
                v.customize ["modifyvm", :id, "--memory", opts[:mem]]
                v.customize ["modifyvm", :id, "--cpus", opts[:cpu]]

            end

        end

    end

end 