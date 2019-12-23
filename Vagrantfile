Vagrant.configure(2) do |config|
    config.vm.box = "generic/ubuntu1804"
    config.vm.box_version = "2.0.6"
    config.vm.define "icebox"

    config.vm.synced_folder ".", "/vagrant", disabled: true

    icebox_local = ''
    config.vm.synced_folder icebox_local, "/vagrant/icebox",
        :nfs => true,
        :nfs_version => 4,
        :nfs_udp => false,
        # speedup NFS with custom options
        :linux__nfs_options => ["rw", "no_subtree_check", "all_squash", "async"]

    rust_local = ''
    config.vm.synced_folder rust_local, "/vagrant/rust",
        :nfs => true,
        :nfs_version => 4,
        :nfs_udp => false,
        # speedup NFS with custom options
        :linux__nfs_options => ["rw", "no_subtree_check", "all_squash", "async"]

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

    config.vm.provision :reload

    config.vm.provision "ansible" do |ansible|
        ansible.compatibility_mode = '2.0'
        # debug
        # ansible.verbose =  '-vvv'
        # ansible.start_at_task =  ''
        ansible.playbook = "ansible/playbook_2.yml"
    end
end

