Vagrant.configure("2") do |config|
  config.vm.box = "spox/ubuntu-arm"
  config.vm.box_version = "1.0.0"
  config.vm.provider "vmware_desktop" do |vmware|
      vmware.gui = true
      vmware.cpus = 2
      vmware.vmx["ethernet0.virtualdev"] = "vmxnet3"
      vmware.ssh_info_public = true
      vmware.linked_clone = false
  end
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update
	  sudo apt install -y make
    sudo apt install -y gcc
    sudo apt install -y libreadline6
    sudo apt install -y libreadline6-dev
	  sudo apt-get install -y zlib1g-dev
	  sudo apt-get install -y bison
	  wget https://ftp.postgresql.org/pub/source/v8.4.22/postgresql-8.4.22.tar.gz
	  tar xfz postgresql-8.4.22.tar.gz
	  cd postgresql-8.4.22
	  ./configure --build=aarch64-unknown-linux-gnu --disable-spinlocks
    make
    sudo make install
	  sudo adduser postgres --gecos "First Last,RoomNumber,WorkPhone,HomePhone" --disabled-password
	  echo "postgres:postgres" | sudo chpasswd
	  sudo mkdir /usr/local/pgsql/data
	  sudo chown postgres /usr/local/pgsql/data
  SHELL
end