FROM mysql:latest
RUN apt-get update && apt-get install -y openvpn apache2 mysql-server php5 php5-mysql nodejs unzip git wget sed npm curl --no-install-recommends \
 && npm install -g bower \
 && ln -s /usr/bin/nodejs /usr/bin/node \
 && rm -rf /var/lib/apt/lists/*
RUN git clone https://github.com/Chocobozzz/OpenVPN-Admin.git \
    &&  mkdir -p /var/www/html/openvpn-admin/include \
    && touch /var/www/html/openvpn-admin/include/config.php \
    && chown -R www-data:www-data /var/www/html/openvpn-admin \
    && cd OpenVPN-Admin && bash update.sh /var/www/html



VOLUME ["/etc/openvpn"]
VOLUME ["/var/www/html"]


RUN echo "\#!/bin/bash" > start.sh \
    && echo "/etc/init.d/mysql start" >> start.sh  \
    && echo "/etc/init.d/apache2 start" >> start.sh \
    && echo "/etc/init.d/openvpn start" >> start.sh \
    && echo "tail -f /var/log/apache2/access.log" >> start.sh \
    && chmod 777 start.sh
    

EXPOSE 80
CMD ["/start.sh"]
