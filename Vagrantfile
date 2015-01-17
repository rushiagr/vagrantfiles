Vagrant.configure("2") do |config|
  config.vm.box = "trusty64"
  config.vm.network "private_network", :type => "dhcp"#,
      #:ip => "192.168.200.0", :netmask => "255.255.255.0"
  config.vm.synced_folder("/home/r/src/devstack", "/home/vagrant/devstack")
  config.vm.synced_folder("/home/r/src/myutils", "/home/vagrant/myutils")
  config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
  end

  config.vm.define :dsold do |cfg|
      cfg.vm.hostname = "dsold.example.com"
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 2500
          v.cpus = 1
      end
  end

  # 'devstack' machine is primarily used for cinder and openstack
  config.vm.define :devstack do |cfg|
      cfg.vm.box = "trusty64"
      cfg.vm.hostname = "devstack.example.com"
      config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
          v.memory = 2500
          v.cpus = 1
      end
  end
  config.vm.define :mdb do |cfg|
      cfg.vm.box = "trusty64"
      cfg.vm.hostname = "mdb.example.com"
      config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
          v.memory = 2200
          v.cpus = 1
      end
  end
  config.vm.define :dsneutron do |cfg|
      cfg.vm.box = "devstack2"
      cfg.vm.hostname = "dsn.example.com"
      config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
          v.memory = 2200
          v.cpus = 1
      end
  end
end
