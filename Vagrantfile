Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  boxes = [
    { name: "api-staging", ip: "192.168.56.10" },
    { name: "payments-staging", ip: "192.168.56.11" },
    { name: "logs-staging", ip: "192.168.56.12" }
  ]

  boxes.each do |box|
    config.vm.define box[:name] do |node|
      node.vm.hostname = box[:name]
      node.vm.network "private_network", ip: box[:ip]
      node.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
        vb.cpus = 1
      end
    end
  end
end
