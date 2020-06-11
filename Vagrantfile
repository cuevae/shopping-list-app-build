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

    sla.vm.network :public_network, bridge: "en0: Wi-Fi (Airport)", ip: "192.168.1.129"

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

    dbh.vm.network :public_network, bridge: "en0: Wi-Fi (Airport)", ip: "192.168.1.81"

  end
  #\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
  # DATABASE server config END
  #\\\\\\\\\\\\\\\\\\\\\\\\\\\\\

end
