BUILD IMAGE FIRST

docker build -t apache .

RUN CONTAINER

docker run -d --name apacheDD -p 80:80 httpd

ENTER CONTAINER

docker exec -it apacheDD /bin/bash

INSTALL LIBS

apt update -y && apt install wget -y && apt install bash -y && apt install nano -y

INSTALL DD LIBS

apt-get install make libssl-dev apache2-dev -y

GO BASH

bash

GET DD FILE & RUN INSTRUCTIONS

rm -f DataDome-Apache-latest.tgz
wget https://package.datadome.co/linux/DataDome-Apache-latest.tgz
tar -zxvf DataDome-Apache-latest.tgz
cd DataDome-ApacheDome-*
make prepare
make
make install # This might required sudo/root access

COPY MOD_DATADOME IN APACHE INSTALLATION

cp docs/mod_datadome.conf /usr/local/apache2/conf

EDIT COPIED FALL AND ADD KEY

nano /usr/local/apache2/conf/mod_datadome.conf

USE FOLLOWING KEY

tcukRE5XiZCumB2

SET HTTP PORT TO 80 AND NOT TO HTTPS

EDIT HTTPD CONF

nano /usr/local/apache2/conf/httpd.conf

UNCOMMENT FOLLOWING LINE : SSL && INCLUDE DATADOME MOD

Include conf/mod_datadome.conf

VERIFY SERVER WORKS

apachectl configtest

RESTART APACHE

apachectl restart