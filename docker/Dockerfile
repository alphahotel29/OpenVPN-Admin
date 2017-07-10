FROM httpd:latest
RUN apt-get update && apt-get install -y php5 php5-mysql nodejs unzip git wget sed npm curl \
 && npm install -g bower \
 && ln -s /usr/bin/nodejs /usr/bin/node \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/alphahotel29/OpenVPN-Admin.git \
 && cd OpenVPN-Admin/docker \
 && ./install-on-docker.sh /var/www/html/ www-data www-data



VOLUME ["/etc/openvpn"]


EXPOSE 80
CMD ["httpd-foreground"]
