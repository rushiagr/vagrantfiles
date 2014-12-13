Vagrant.configure("2") do |config|
  config.vm.box = "trusty64"
  config.vm.network "private_network", :type => "dhcp"#,
      #:ip => "192.168.200.0", :netmask => "255.255.255.0"
  config.vm.synced_folder("/home/r/src/myutils", "/home/vagrant/myutils")
  config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
  end

  config.vm.define :devstack do |cfg|
      cfg.vm.hostname = "node1.example.com"
      cfg.vm.synced_folder("/home/r/src/python-openstackclient", "/opt/stack/python-openstackclient")
      cfg.vm.synced_folder("/home/r/src/keystone", "/opt/stack/keystone")
      cfg.vm.synced_folder("/home/r/src/python-keystoneclient", "/opt/stack/python-keystoneclient")
      cfg.vm.synced_folder("/home/r/src/glance", "/opt/stack/glance")
      cfg.vm.synced_folder("/home/r/src/python-keystoneclient", "/opt/stack/python-keystoneclient")
      cfg.vm.synced_folder("/home/r/src/cinder", "/opt/stack/cinder")
      cfg.vm.synced_folder("/home/r/src/python-cinderclient", "/opt/stack/python-cinderclient")
      cfg.vm.synced_folder("/home/r/src/cinder", "/opt/stack/cinder")
      cfg.vm.synced_folder("/home/r/src/devstack", "/opt/stack/devstack")
      config.vm.provider "virtualbox" do |v|
          v.memory = 3333
          v.cpus = 1
      end
  end
  config.vm.define :dsneutron do |cfg|
      cfg.vm.hostname = "dsneutron.example.com"
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 2300
          v.cpus = 1
      end
  end
end
