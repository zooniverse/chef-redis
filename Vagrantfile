# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.hostname = "redis-berkshelf"

  config.vm.box = "opscode_ubuntu-13.10"
  config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-13.10_chef-provisionerless.box"

  config.vm.network :private_network, ip: "33.33.33.10"

  config.berkshelf.enabled = true
  config.omnibus.chef_version = :latest

  config.vm.provision :chef_solo do |chef|
    chef.json = {
      redis: {
        instances: [
          {
            port: 6379,
            password: 'test',
            dir: '/redis6379'
          },
          {
            port: 6380,
            password: 'test2',
            dir: '/redis6379'
          }
        ]
      }
    }

    chef.run_list = [
      "recipe[redis::default]",
    ]
  end
end
