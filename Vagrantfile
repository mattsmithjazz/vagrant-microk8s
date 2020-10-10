IMAGE_NAME = "generic/ubuntu2004"
N = 2

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.vm.provider "virtualbox" do |v|
        v.memory = 2048
        v.cpus = 2
    end

    config.vm.define "master" do |master|
      master.vm.box = IMAGE_NAME
      master.vm.network "private_network", ip: "192.168.50.10"
      config.vm.network "forwarded_port", guest: 16443, host: 16443,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 10250, host: 10250,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 10255, host: 10255,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 25000, host: 25000,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 12379, host: 12379,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 10257, host: 10257,
        auto_correct: true
      config.vm.network "forwarded_port", guest: 10259, host: 10259,
        auto_correct: true

        
      
      master.vm.hostname = "master"
      master.vm.provision "ansible", type:'ansible' do |ansible|
          ansible.playbook = "master-playbook.yml"
          ansible.extra_vars = {
              worker_ip: "192.168.50.10",
          }
      end
   end 

              
          config.vm.define "worker" do |worker|
          worker.vm.box = IMAGE_NAME
          worker.vm.network "private_network", ip: "192.168.50.11"
          worker.vm.hostname = "worker"
          worker.vm.provision "ansible" do |ansible|
              ansible.playbook = "worker-playbook.yml"
              ansible_extra_vars = {
                  worker_ip: "192.168.50.11",
              }
          end
      end
  end


