Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.provision "ansible_local" do |ansible|
    ansible.inventory_path = "tests/inventory"
    ansible.limit = "localhost"
    ansible.playbook = "tests/test.yml"
    ansible.raw_arguments = [
        "--connection=local",
        "--sudo",
    ]
    ansible.verbose = "v"
  end

end
