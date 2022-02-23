# middleware-scripts
#!/bin/bash

#Author: Njike
#Date: Feb 22 2022

echo "Installation and configure of SonarQube on CentOS 7"

sleep 3

echo "Step 1: Java 11 installation"

sleep 3

sudo yum update -y

sudo yum install java-11-openjdk-devel -y

sudo yum install java-11-openjdk -y

sleep 3

echo "Step 2: Download SonarQube latest versions on your server"

sleep 3

cd /opt

sudo yum install wget -y

sudo wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-9.3.0.51899.zip

sleep 3

echo "Step 3: Extract packages"

sleep 3

sudo yum install unzip -y

sudo unzip /opt/sonarqube-9.3.0.51899.zip

sleep 3

echo "Step 4: Change ownership to the user and Switch to Linux binaries directory to start service"

sleep 3

sudo chown -R vagrant:vagrant /opt/sonarqube-9.3.0.51899

cd /opt/sonarqube-9.3.0.51899/bin/linux-x86-64

./sonar.sh start

sleep 3

echo "Opening port 900"

sleep 3

sudo firewall-cmd --permanent --add-port=9000/tcp

sudo firewall-cmd --reload

sleep 3

echo "Sonarqube installed and started successfully"
