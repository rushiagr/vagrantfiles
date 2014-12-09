Vagrant.configure("2") do |config|
  config.vm.box = "trusty64"
  config.vm.network "private_network", :type => "dhcp"#,
      #:ip => "192.168.200.0", :netmask => "255.255.255.0"
  config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
  end

  config.vm.define :devstack do |cfg|
      cfg.vm.hostname = "node1.example.com"
      cfg.vm.synced_folder("/home/r/src/", "/opt/stack/")
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
