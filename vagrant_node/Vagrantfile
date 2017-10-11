#PLUGIN
#vagrant plugin install vagrant-hostsupdater

Vagrant.configure("2") do |config|

  config.vm.define "myvirtualmachine" do |myvirtualmachine|
    # base template for virtualbox
    myvirtualmachine.vm.box = "hashicorp/precise64"

    # domain on which our application will respond later on
    myvirtualmachine.vm.hostname = "myvirtualmachine.dev"

    # ip address will be used by the vm
    # myvirtualmachine.vm.network :private_network, ip: "192.168.33.151"

    myvirtualmachine.vm.provision "ansible" do |ansible|
     ansible.playbook = "provisioning/playbook.yml"
    end

  end

  # Access the shared vagrant directory via NFS, otherwise slow on Mac and windows
  # config.vm.synced_folder ".",  "/vagrant", type: "nfs"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end
end
