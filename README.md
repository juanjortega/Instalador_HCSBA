# Instalador

yum install -y https://kojipkgs.fedoraproject.org//packages/zlib/1.2.11/19.fc30/x86_64/zlib-1.2.11-19.fc30.x86_64.rpm

yum install epel-release

yum install python-pip

pip install pip==v19.0

uninstall click

pip install click==v7.0

pip install pyusb

pip install babel==v0.9.6

pip install decorator==v3.4.0

pip install beautifulsoup4

yum install http://repo.mybahmni.org/releases/ansible-2.4.6.0-1.el7.ans.noarch.rpm
yum install http://repo.mybahmni.org.s3.amazonaws.com/rpm/bahmni/bahmni-installer-0.93-151.noarch.rpm

# sacar setup y local del repositorio

curl -L https://github.com/Lopior/Instalador/edit/main/setup.yml >> /etc/bahmni-installer/setup.yml

curl -L https://github.com/Lopior/Instalador/edit/main/local >> /etc/bahmni-installer/local

echo "export BAHMNI_INVENTORY=local" >> ~/.bashrc
source ~/.bashrc

bahmni install 

curl -L https://github.com/Lopior/Instalador/edit/main/email-notification.properties >> /opt/openmrs/email-notification.properties


