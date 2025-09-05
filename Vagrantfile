Vagrant.configure('2') do |config|
  config.vbguest.auto_update = false
  config.ssh.insert_key = false
  # config.vbguest.no_remote = true
  config.vm.box = "ubuntu/focal64"
  if Vagrant.has_plugin?('vagrant-cachier')
    config.cache.scope = 'machine'
  end
  config.vm.cloud_init :user_data do |cloud_init|
    cloud_init.content_type = "text/cloud-config"
    cloud_init.path = "config.cfg"
  end
  config.vm.provider "virtualbox" do |virtualbox, override|
    virtualbox.memory = 1024
    virtualbox.cpus = 2
    virtualbox.linked_clone = true
  end
  ["gateway", "frontend", "backend", "database"].each_with_index do |name, i|
    config.vm.define name do |c|
      c.vm.hostname = "#{name}"
      c.vm.network "private_network", ip: "192.168.56.#{10+i}", type: "static"
    end
  end
end