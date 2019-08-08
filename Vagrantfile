Vagrant.configure(2) do |config|
    config.vm.box = "generic/debian10"
    config.vm.define "icebox"

    config.vm.synced_folder ".", "/vagrant", disabled: true

    icebox_local = 'FILL_ME'
    config.vm.synced_folder icebox_local, "/vagrant/icebox",
        :nfs => true,
        :nfs_version => 4,
        :nfs_udp => false

    config.vm.provider :libvirt do |libvirt|
        libvirt.cpus = 4
        libvirt.memory = 2048
        libvirt.nic_model_type = "virtio"
        libvirt.driver = "kvm"
        libvirt.nested = true
    end

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = '2.0'
        # debug
        # ansible.verbose =  '-vvv'
        # ansible.start_at_task =  ''
        ansible.playbook = "ansible/playbook_1.yml"
    end

    # config.vm.provision :reload

    # config.vm.provision "ansible" do |ansible|
    #     ansible.compatibility_mode = '2.0'
    #     # debug
    #     # ansible.verbose =  '-vvv'
    #     # ansible.start_at_task =  ''
    #     ansible.playbook = "ansible/playbook_2.yml"
    #     ansible.extra_vars = {
    #         'root_dir': root_dir,
    #     }
    # end
end

