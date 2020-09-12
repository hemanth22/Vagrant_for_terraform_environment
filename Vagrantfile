Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/centos8"
  #config.ssh.insert_key = false
  config.vm.hostname = "terraform"
  config.vm.network "private_network", ip: "193.168.33.55"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.limit = "all"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.become = true
    ansible.extra_vars = { ansible_python_interpreter: '/usr/bin/python3' }
  end
end
