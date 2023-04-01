1  sudo apt update
    2  sudo apt install default-jdk -y
    3  java --version
    4  sudo apt install curl wget -y
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
   18  sudo systemctl start wildfly
   19  sudo systemctl enable wildfly
   20  sudo systemctl status wildfly
   21  ss -tunelp | grep 8080
   22  sudo /opt/wildfly/bin/add-user.sh
   23  cat >> ~/.bashrc <<EOF
export WildFly_BIN="/opt/wildfly/bin/"
export PATH=\$PATH:\$WildFly_BIN
EOF

   24  source ~/.bashrc
   25  jboss-cli.sh --connect
   26  ss -tunelp | grep 9990
   27  sudo vim /opt/wildfly/bin/launch.sh
   28  sudo systemctl restart wildfly
   29  systemctl status  wildfly
   30  ss -tunelp | grep 9990
