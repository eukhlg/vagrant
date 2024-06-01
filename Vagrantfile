Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian12"
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
	sudo apt-get install -y make
    sudo apt-get install -y gcc
	sudo apt-get install -y libreadline6 libreadline6-dev
	sudo apt-get install -y zlib1g-dev
	sudo apt-get install -y bison
	wget https://ftp.postgresql.org/pub/source/v8.4.22/postgresql-8.4.22.tar.gz
	tar xfz postgresql-8.4.22.tar.gz
	cd postgresql-8.4.22
	./configure
    make
    sudo make install
	sudo adduser postgres --gecos "First Last,RoomNumber,WorkPhone,HomePhone" --disabled-password
	echo "postgres:postgres" | sudo chpasswd
	sudo mkdir /usr/local/pgsql/data
	sudo chown postgres /usr/local/pgsql/data
  SHELL
end
