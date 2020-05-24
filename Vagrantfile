Vagrant.configure("2") do |config|
  
  #========================
  # ALL servers config START
  #========================
  config.vm.box = "ubuntu/focal64"
  #\\\\\\\\\\\\\\\\\\\\\\\\
  # ALL servers config END
  #\\\\\\\\\\\\\\\\\\\\\\\\

  #========================
  # APP server config START
  #========================
  config.vm.define "sla-host" do |sla|

    sla.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end

    sla.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbooks/main.yml"
      ansible.become = true
      ansible.become_user = "root"
    end

    sla.vm.network "private_network", ip: "192.168.10.10"
    sla.vm.network "forwarded_port", guest:19000, host: 8080
    sla.vm.network "forwarded_port", guest:19001, host: 8081
    sla.vm.network "forwarded_port", guest:19002, host: 8082
    sla.vm.network "forwarded_port", guest:19006, host: 8086

    #Folder automated sync between host and guest machine
    sla.vm.synced_folder "shopping-list-app/", "/vagrant/shopping-list-app", create: true
  end
  #\\\\\\\\\\\\\\\\\\\\\\\\
  # APP server config END
  #\\\\\\\\\\\\\\\\\\\\\\\\

  #=============================
  # DATABASE server config START
  #=============================
  config.vm.define "db-host" do |dbh|

    dbh.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end

    dbh.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbooks/main.yml"
      ansible.become = true
      ansible.become_user = "root"
    end

    dbh.vm.network "private_network", ip: "192.168.10.20"

  end
  #\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
  # DATABASE server config END
  #\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

end
