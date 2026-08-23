---

---
```bash
# Versão
vagrant version

#Cria um Vagrantfile para a imagem precise64 (ubuntu)
vagrant init hashicorp/precise64
vagrant up
vagrant status
vagrant halt
vagrant reload
vagrant destroy

# Abre uma conexão ssh para a máquina virtual (necessário estar dentro da pasta do projeto, contendo o respectivo vagrantfile
vagrant ssh
vagrant ssh-config

# Provisionamento.
# Adicionar as linhas de provisionamento no Vagrantfile:
Vagrant.configure("2") do |config|
    config.vm.provision "shell",
        inline: "echo hello, World"
end

#Rodar no Shell
vagrant provision
```

```bash
# Basico
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "forwarded_port", guest: 80, host: 8089
  config.vm.network "public_network", ip: "192.168.1.24"
	config.vm.provision "shell",
        inline: "cat id_bionic.pub >> .ssh/authorized_keys"
	config.vm.synced_folder "./configs", "/configs"
	config.vm.synced_folder ".", "/vagrant", disabled: true
end

# Com provisionamento
$script_mysql = <<-SCRIPT
  apt-get update && \
  apt-get install -y mysql-server-5.7 && \
  mysql -e "create user 'phpuser'@'%' identified by 'pass';"
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"

  config.vm.network "forwarded_port", guest: 80, host: 8089
  config.vm.network "public_network", ip: "192.168.1.24"

  config.vm.provision "shell", inline: "cat /configs/id_bionic.pub >> .ssh/authorized_keys"

  config.vm.provision "shell", inline: $script_mysql
  config.vm.provision "shell", inline: "cat /configs/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf"
  config.vm.provision "shell", inline: "service mysql restart"

  config.vm.synced_folder "./configs", "/configs"
  config.vm.synced_folder ".", "/vagrant", disabled: true
end

# Scripts de provisionamento externos
Vagrant.configure("2") do |config|  
	config.vm.provision "shell", path: "script.sh"
end

# Ambiente Multimachine

Vagrant.configure ("2") do |config|
	config.vm.box = "ubuntu/bionic64"

  config.vm.define "mysqldb" do |mysql|
		(...)
	end

	config.vm.define "phpweb" do |phpweb|
	  phpweb.vm.network "forwarded_port", guest:80, host:8089
    phpweb.vm.network "public_network", ip: "192.168.1.25"
  end

end
```

```bash
# Gere um par de chaves com a ferramenta keygen
ssh-keygen -t rsa

# Acesse a máquina virtual:
vagrant ssh

# Dentro da máquina virtual, visualize a pasta vagrant que é um compartilhamento da pasta em seu computador local:
ls /vagrant

# Agora, copie a chave pública da pasta local vagrant para a máquina virtual:
cp /vagrant/id_bionic.pub .

# Adicione a chave pública na máquina virtual, no arquivo .ssh/authorized_keys
cat id_bionic.pub >> .ssh/authorized_keys

# Teste a conexão SSH com as chaves geradas:
ssh -i sua_chave_privada vagrant@seu-ip
```