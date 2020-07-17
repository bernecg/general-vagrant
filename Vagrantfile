# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-'SCRIPT'

echo "Install some tools..."
sudo apt update && \
sudo apt install -y unzip \
                    python3-pip \
                    python3-venv \
                    openjdk-8-jdk

echo "Terraform setup..."
if [ ! -f /usr/local/bin/terraform ]; then
  TF_VERSION=0.12.28
  wget https://releases.hashicorp.com/terraform/${TF_VERSION}/terraform_${TF_VERSION}_linux_amd64.zip
  unzip terraform_${TF_VERSION}_linux_amd64.zip
  sudo mv terraform /usr/local/bin/
  rm terraform_${TF_VERSION}_linux_amd64.zip
fi
terraform --version

SCRIPT

Vagrant.configure("2") do |config|
  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/bionic64"

  # Disksize
  config.disksize.size = '30GB'

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.99"

  # Shared folders
  config.vm.synced_folder "<HOST PATH>", "<GUEST PATH>"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.cpus = "2"
  end

  config.vm.provision "shell", inline: $script
  config.vm.provision :docker
end
