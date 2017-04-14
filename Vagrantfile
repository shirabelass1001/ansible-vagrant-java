# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "opscode-centos-6.3"
  # ローカルに無ければ取ってくる
  config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.3-x86_64-v20130101.box"
  config.vm.hostname = "webserver"
  config.vbguest.auto_update = false

  config.vm.network :forwarded_port, guest: 8443, host: 3000
  config.vm.network :private_network, ip: "192.168.33.10"

  config.vm.synced_folder "./www/tomcat/webapps", "/var/www/tomcat/webapps"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.inventory_path = "hosts"
    ansible.limit = "all"
    ansible.verbose = "v"
  end

end
