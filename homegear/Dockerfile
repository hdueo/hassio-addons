FROM debian:buster-slim
MAINTAINER Dr. Sathya Laufer <sathya@homegear.email>
RUN apt-get update && apt-get -y install apt-transport-https apt-utils wget ca-certificates gnupg libzip4 libavahi-client3 libavahi-client-dev insserv
RUN touch /tmp/HOMEGEAR_STATIC_INSTALLATION; \
wget https://apt.homegear.eu/Release.key && apt-key add Release.key && rm Release.key; \
echo 'deb https://apt.homegear.eu/Debian/ buster/' >> /etc/apt/sources.list.d/homegear.list; \
apt-get update && apt-get -y install libhomegear-node homegear homegear-management homegear-webssh homegear-adminui homegear-ui homegear-nodes-core homegear-nodes-extra homegear-homematicbidcos homegear-homematicwired homegear-insteon homegear-max homegear-philipshue homegear-sonos homegear-kodi homegear-ipcam homegear-beckhoff homegear-knx homegear-enocean homegear-intertechno homegear-rsl homegear-rs2w homegear-mbus homegear-zwave homegear-zigbee homegear-ccu homegear-easyled homegear-easyled2 homegear-easycam homegear-influxdb; \
rm -f /etc/homegear/dh1024.pem; \ 
rm -f /etc/homegear/homegear.crt; \
rm -f /etc/homegear/homegear.key; \
cp -R /etc/homegear /etc/homegear.config; \
cp -R /var/lib/homegear /var/lib/homegear.data; \
apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* 



COPY script/run.sh /run.sh
RUN chmod +x /run.sh
ENTRYPOINT ["/bin/bash", "-c", "/run.sh"]

EXPOSE 2001 2002 2003
