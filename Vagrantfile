Vagrant.configure("2") do |config|

    N = 1
    (1..N).each do |machine_id|
      config.vm.define "machine#{machine_id}" do |machine|

        machine.vm.box =  "generic/centos8"

        machine.ssh.insert_key = false
        machine.vm.provision "file", source: "./id_rsa.pub", destination: "~/.ssh/authorized_keys"
        machine.ssh.private_key_path = ["./id_rsa", "~/.vagrant.d/insecure_private_key"]
        machine.vm.hostname = "machine#{machine_id}"
        machine.vm.provision "shell", inline: "yum update -y"

        if machine_id == 1
          machine.vm.provider "parallels" do |prl|
            prl.cpus = "1"
            prl.memory = "512"
            prl.update_guest_tools = true
          end
        end

        if machine_id > 1
          machine.vm.provider "paralles" do |prl|
            prl.cpus = "1"
            prl.memory = "512"
            prl.update_guest_tools = true
          end
        end

      end
    end

end
