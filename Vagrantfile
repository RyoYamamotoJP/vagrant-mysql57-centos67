Vagrant.configure(2) do |config|
  config.vm.box = 'bento/centos-6.7'
  config.vm.provision :shell, inline: <<-SHELL
    sudo rpm --import http://dev.mysql.com/doc/refman/5.7/en/checking-gpg-signature.html
    sudo rpm -Uvh http://dev.mysql.com/get/mysql57-community-release-el6-7.noarch.rpm
    sudo yum install -y mysql-community-server
    sudo yum update -y
    cat << EOF | sudo tee -a /etc/my.cnf
character-set-server=utf8mb4
collation-server=utf8mb4_unicode_ci
[client]
default-character-set=utf8mb4
EOF
    sudo service mysqld start
    sudo grep 'temporary password' /var/log/mysqld.log
  SHELL
end
