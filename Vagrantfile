Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/centos8"
  #config.ssh.insert_key = false
  config.vm.hostname = "terraform"
  config.vm.network "private_network", ip: "193.168.33.55"
  for i in 81..89
          config.vm.network :forwarded_port, guest: i, host: i
  end

  for i in 8080..8089
          config.vm.network :forwarded_port, guest: i, host: i
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.limit = "all"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.become = true
    ansible.extra_vars = { ansible_python_interpreter: '/usr/bin/python3' }
  end
end
