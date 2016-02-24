# -*- mode: ruby -*-
# vi: set ft=ruby :

pxc_nodes = 3

Vagrant.configure(2) do |config|

  config.vm.box = "bento/centos-6.7"

  (1..pxc_nodes).each do |i|
    pxc_node_name = "pxc-node-"+ i.to_s
    config.vm.define pxc_node_name do |node|
      node.vm.hostname = pxc_node_name
      node.vm.network :private_network, type: "dhcp"

      node.vm.provider 'virtualbox' do |vb|
        vb.cpus = 1
        vb.memory = 512
        vb.linked_clone = true if Vagrant::VERSION =~ /^1.8/
        vb.customize ["createhd",  "--filename", ".vagrant/#{pxc_node_name}.vmdk", "--size", 20 * 1024]
        vb.customize ["storageattach", :id, "--storagectl", "SATA Controller", "--port", "1", "--type", "hdd", "--medium", ".vagrant/#{pxc_node_name}.vmdk"]
      end

      if i == pxc_nodes
        node.vm.provision :ansible do |ansible|
          ansible.limit = "all"
          ansible.playbook = "provisioning/playbook.yml"
          ansible.groups = {
            "percona_cluster" => [ "pxc-node-[1:#{pxc_nodes}]"]
          }
        end
      end
    end
  end

end
