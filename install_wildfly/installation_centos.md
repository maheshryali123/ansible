1  sudo yum update
    2  sudo yum install java-11-openjdk-devel
    3  sudo yum -y install wget curl
    4  history
    5  WILDFLY_RELEASE=$(curl -s https://api.github.com/repos/wildfly/wildfly/releases/latest|grep tag_name|cut -d '"' -f 4)
    6  wget https://github.com/wildfly/wildfly/releases/download/${WILDFLY_RELEASE}/wildfly-${WILDFLY_RELEASE}.tar.gz
    7  tar xvf wildfly-${WILDFLY_RELEASE}.tar.gz
    8  sudo mv wildfly-${WILDFLY_RELEASE} /opt/wildfly
    9  sudo groupadd --system wildfly
   10  sudo useradd -s /sbin/nologin --system -d /opt/wildfly  -g wildfly wildfly
   11  sudo mkdir /etc/wildfly
   12  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/wildfly.conf /etc/wildfly/
   13  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/wildfly.service /etc/systemd/system/
   14  sudo cp /opt/wildfly/docs/contrib/scripts/systemd/launch.sh /opt/wildfly/bin/
   15  sudo chmod +x /opt/wildfly/bin/launch.sh
   16  sudo chown -R wildfly:wildfly /opt/wildfly
   17  sudo systemctl daemon-reload
   18  sudo semanage fcontext  -a -t bin_t  "/opt/wildfly/bin(/.*)?"
   19  sudo restorecon -Rv /opt/wildfly/bin/
   20  history
   21  sudo systemctl start wildfly
   22  sudo systemctl enable wildfly
   23  systemctl status wildfly
   24  sudo systemctl status wildfly
   25  sudo systemctl enable wildfly
   26  sudo systemctl status wildfly
   27  history
   28  sudo systemctl enable wildfly
   29  sudo systemctl status wildfly
   30  history
   31  sudo systemctl status wildfly.service
   32  sudo systemctl start wildfly.service
   33  sudo systemctl status wildfly.service
   34  dnf install -y wildfly
   35  sudo yum install dnf
   36  dnf install -y wildfly
   37  sudo dnf install -y wildfly
   38  ls
   39  cd /var
   40  ls
   41  cd lib
   42  ls
   43  wildfly -v
   44  cd  /opt/wildfly
   45  ls
   46  cd ~
   47  sudo ss -tunelp | grep 8080
   48  sudo /opt/wildfly/bin/add-user.sh
   49  java --version
   50  java -version
   51  history
   52  sudo yum install java-11-openjdk-devel
   53  sudo systemctl status wildfly.service
   54  sudo systemctl enable wildfly
   55  sudo systemctl restart wildfly
   56  sudo systemctl enable wildfly
   57  sudo systemctl status wildfly
   58  sudo ss -tunelp | grep 8080
   59  sudo /opt/wildfly/bin/add-user.sh
   60  cat >> ~/.bashrc <<EOF
export WildFly_BIN="/opt/wildfly/bin/"
export PATH=\$PATH:\$WildFly_BIN
EOF

   61  source ~/.bashrc
   62  jboss-cli.sh --connect
   63  sudo ss -tunelp | grep 9990
   64  vi /opt/wildfly/bin/launch.sh
   65  sudo chmod 777 /opt/wildfly/bin/launch.sh
   66  vi /opt/wildfly/bin/launch.sh
   67  sudo systemctl restart wildfly
   68  ss -tunelp | grep 9990
   69  sudo firewall-cmd --permanent --add-port={8080,9990}/tcp
   70  sudo yum install firewall-cmd
   71  sudo firewall-cmd --permanent --add-port={8080,9990}/tcp



   referehere:https://computingforgeeks.com/how-to-install-wildfly-jboss-on-rhel-centos/