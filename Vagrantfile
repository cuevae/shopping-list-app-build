Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.define "shopping-list-app" do |sla|
    sla.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    sla.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbooks/main.yml"
      ansible.become = true
      ansible.become_user = "root"
    end
    #browser port forwarding
    sla.vm.network "forwarded_port", guest:19000, host: 8080
    sla.vm.network "forwarded_port", guest:19001, host: 8081
    sla.vm.network "forwarded_port", guest:19002, host: 8082
    sla.vm.network "forwarded_port", guest:19006, host: 8086
    #Folder automated sync between host and guest machine
    sla.vm.synced_folder "shopping-list-app/", "/vagrant/shopping-list-app"
  end
end