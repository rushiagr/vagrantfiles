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

  # Multi=node devstack
  config.vm.define :dsneutron do |cfg|
      cfg.vm.box = "devstack2"
      cfg.vm.hostname = "dsn.example.com"
      config.vm.provider "virtualbox" do |v|
          v.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
          v.memory = 2200
          v.cpus = 1
      end
  end
    config.vm.define :mncontroller do |controller_config|
        controller_config.vm.box = "devstack2"
        controller_config.vm.host_name = "controller.example.com"
        controller_config.vm.network :private_network, ip:"192.168.100.10"
        controller_config.vm.network :private_network, ip:"192.168.200.10"
		config.vm.provider :virtualbox do |vb|
		    vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
            vb.customize ["modifyvm", :id, "--memory", "3000"]
            vb.customize ["modifyvm", :id, "--cpus", "2"]
			# vb.gui = true
        end
    end

    config.vm.define :mncompute1 do |compute1_config|
        compute1_config.vm.box = "devstack2"
        compute1_config.vm.host_name = "compute1.example.com"
        compute1_config.vm.network :private_network, ip:"192.168.100.30"
        compute1_config.vm.network :private_network, ip:"192.168.200.30"
        config.vm.provider :virtualbox do |vb|
		    vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
            vb.customize ["modifyvm", :id, "--memory", "1500"]
            vb.customize ["modifyvm", :id, "--cpus", "2"]
			# vb.gui = true
        end
    end

    config.vm.define :mnaccess do |access_config|
        access_config.vm.box = "trusty64"
        access_config.vm.host_name = "access.example.com"
        access_config.vm.network :private_network, ip:"192.168.100.40"
        access_config.vm.network :private_network, ip:"192.168.200.40"
        config.vm.provider :virtualbox do |vb|
            vb.customize ["modifyvm", :id, "--memory", "256"]
            vb.customize ["modifyvm", :id, "--cpus", "1"]
			# vb.gui = true
        end
    end
end
