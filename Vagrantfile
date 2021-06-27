Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.ssh.insert_key = false
  config.vm.synced_folder ".","/vagrant", disabled: true
  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.linked_clone = true
  end
  config.vm.define "app1" do |app|
      app.vm.hostname = "app1.test"
      app.vm.network :private_network, ip:"192.168.60.6"
  end
  config.vm.define "db1" do |db|
    db.vm.hostname = "db1.test"
    db.vm.network :private_network, ip: "192.168.60.7"
  end
end
