FROM debian:jessie
RUN apt-get update && apt-get install -y openvpn apache2 mysql-server php5 php5-mysql php5 nodejs unzip git wget sed npm curl \
 && npm install -g bower \
 && ln -s /usr/bin/nodejs /usr/bin/node \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/Chocobozzz/OpenVPN-Admin.git \
 && cd OpenVPN-Admin \
 && ./install.sh /var/www/html/ www-data www-data

VOLUME ["/etc/openvpn"]
EXPOSE 1194/udp
EXPOSE 443/tcp

CMD "apache& mysql-server& openvpn"
