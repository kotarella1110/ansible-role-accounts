Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.synced_folder "./", "/etc/ansible/roles/kotarella1110.users", create: true

  config.vm.provision "ansible_local" do |ansible|
    ansible.inventory_path = "tests/inventory"
    ansible.limit = "localhost"
    ansible.playbook = "tests/test.yml"
  end

end
