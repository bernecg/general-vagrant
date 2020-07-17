# Multipurpose Vagrant box
Box with several tools installed used for multiple
purpose but mostly focused on development.

## Requirements
Configuration `config.disksize.size` needs plugin `vagrant-disksize`. Install it by using the following command:
```
vagrant plugin install vagrant-disksize
```

Besides, you need to delete or add the configuration
to share folders between the Host and the Guest.

## Installed tools
The tools that are currently being installed are:
  * unzip
  * python3-pip
  * python3-venv
  * openjdk 8
  * terraform 0.12.28
  * docker
