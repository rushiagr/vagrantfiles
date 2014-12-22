Vagrant.configure("2") do |config|
  config.vm.box = "trusty64"
  config.vm.network "private_network", :type => "dhcp"#,
      #:ip => "192.168.200.0", :netmask => "255.255.255.0"
  config.vm.synced_folder("/home/r/src/myutils", "/home/vagrant/myutils")
  config.vm.provider "virtualbox" do |v|
      v.memory = 1024
      v.cpus = 1
  end

  config.vm.define :dsn do |cfg|
      cfg.vm.hostname = "dsn.example.com"
#      for repo in ['keystone', 'cinder', 'nova', 'glance', 'neutron',
#                'python-keystoneclient', 'python-cinderclient', 'python-novaclient',
#                'python-glanceclient', 'python-neutronclient', 'python-openstackclient',
#                'devstack']
#          cfg.vm.synced_folder("/home/r/src/#{repo}", "/opt/stack/#{repo}")
#      end
      cfg.vm.synced_folder("/home/r/src/devstack", "/opt/stack/devstack")
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 4000
          v.cpus = 2
      end
  end
  config.vm.define :dsn2 do |cfg|
      cfg.vm.hostname = "dsn2.example.com"
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 4000
          v.cpus = 2
      end
  end
  config.vm.define :ds do |cfg|
      for repo in ['keystone', 'cinder', 'nova', 'glance', 'neutron',
                'python-keystoneclient', 'python-cinderclient', 'python-novaclient',
                'python-glanceclient', 'python-neutronclient', 'python-openstackclient',
                'devstack']
          cfg.vm.synced_folder("/home/r/src/#{repo}", "/home/vagrant/#{repo}")
      end
      cfg.vm.synced_folder("/home/r/src/devstack", "/opt/stack/devstack")
      cfg.vm.hostname = "ds.example.com"
      config.vm.provider "virtualbox" do |v|
          v.memory = 2000
          v.cpus = 1
      end
  end
  config.vm.define :dsold do |cfg|
      cfg.vm.hostname = "dsold.example.com"
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 2500
          v.cpus = 1
      end
  end
  config.vm.define :ds2 do |cfg|
      # Trying out latest devstack from old devstack to see if it works
      cfg.vm.hostname = "ds2.example.com"
      cfg.vm.box = 'devstack'
      config.vm.provider "virtualbox" do |v|
          v.memory = 2500
          v.cpus = 1
      end
  end
end
