Vagrant.configure(2) do |config|

  N = 2
  (1..N).each do |i|
    config.vm.define "haproxy#{i}" do |node|
      node.vm.box = "ubuntu/jammy64"
      node.vm.synced_folder ".", "/vagrant", disabled: true
      node.vm.hostname = "haproxy#{i}"
      node.vm.network "private_network", ip:"10.0.26.20#{i}"
      node.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.name = "haproxy#{i}"
        vb.cpus = 2
      end
    end
  end

  (1..N).each do |i|
    config.vm.define "web#{i}" do |app|
      app.vm.network "private_network", ip:"10.0.26.10#{i}"
      app.vm.hostname = "app#{i}"
      app.vm.box = "ubuntu/jammy64"
      app.vm.synced_folder ".", "/vagrant", disabled: true
      app.vm.box_check_update = false
      app.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.name = "web#{i}"
        vb.cpus = 2
      end
  end
end

end