# Instalador

sudo yum install -y https://kojipkgs.fedoraproject.org//packages/zlib/1.2.11/19.fc30/x86_64/zlib-1.2.11-19.fc30.x86_64.rpm

sudo yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

sudo yum install python-pip

sudo pip install pip==v19.0

pip install --upgrade pip

pip install babel==v1.0 python-stdnum urllib3==1.21.1 idna==2.5 chardet==3.0.2 certifi==2017.4.17 qrcode pyserial pypdf python-chart psycogreen passlib ofxparse requests

# sudo uninstall click

# sudo pip install click==v7.0

# sudo pip install pyusb

# sudo pip install babel==v0.9.6

# sudo pip install decorator==v3.4.0

# sudo pip install beautifulsoup4

# sudo yum install http://repo.mybahmni.org/releases/ansible-2.4.6.0-1.el7.ans.noarch.rpm

sudo yum install http://repo.mybahmni.org.s3.amazonaws.com/rpm/bahmni/bahmni-installer-0.93-151.noarch.rpm

# sacar setup y local del repositorio

sudo wget https://raw.githubusercontent.com/Lopior/Instalador/main/Setup.yml /etc/bahmni-installer/setup.yml

sudo wget https://raw.githubusercontent.com/Lopior/Instalador/main/local  /etc/bahmni-installer/local

echo "export BAHMNI_INVENTORY=local" >> ~/.bashrc
source ~/.bashrc

yum install http://mirror.centos.org/centos/7/extras/x86_64/Packages/centos-release-scl-rh-2-3.el7.centos.noarch.rpm
yum install https://rpmfind.net/linux/centos/7.9.2009/extras/x86_64/Packages/centos-release-scl-2-3.el7.centos.noarch.rpm


sudo bahmni -i local install 

sudo curl -L https://github.com/Lopior/Instalador/edit/main/email-notification.properties >> /opt/openmrs/email-notification.properties


# modificar patient name regex de openmrs ^[a-zA-Zñáéíóúü \-]+$

# modificar expresion en app.json en regustration.  "middleName" : {"pattern" : "[a-zA-Zñáéíóúü\\s]{0,}", "errorMessage" : "Should contain characters"},

#backup de bahmni. total

 bahmni -i local backup --backup_type=all --options=all

#restaurar bahmni
#archivos quedan en /data/ y en /home/bahmni que deben ponerse a mano en maquina destino.

bahmni -i local restore --restore_type=db --options=openmrs --strategy=dump   --restore_point=openmrs_dump_20170221084218.sql.gz


