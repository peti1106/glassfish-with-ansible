PROXY = "http://proxy1.sulzer.de:88"


Vagrant.configure("2") do |config|
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http      = PROXY
    config.proxy.https     = PROXY
    config.proxy.ftp       = PROXY
    config.apt_proxy.http  = PROXY
    config.apt_proxy.https = PROXY
    config.proxy.no_proxy  = "localhost,127.0.0.1,.example.com"
  end

  config.vm.box = "hashicorp/precise64"
  config.vm.network "private_network", ip: "192.168.33.10"

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "site.yml"
    ansible.install = true
    ansible.install_mode = :pip
    ansible.version = "2.2"
  end
end
