# Run on Ubuntu 16.04
FROM ubuntu:16.04

# Install system dependencies
RUN apt-get update
RUN apt-get install -y git python build-essential curl mongodb supervisor
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - 
RUN apt-get install -y nodejs
RUN mkdir -p /var/www
RUN mkdir -p /var/log/supervisor
RUN npm install -g sails


# Install production map server
RUN git clone https://github.com/ProductionMap/production-map-server.git /var/www/production-map-server
WORKDIR /var/www/production-map-server/production-map-server
RUN npm install

# Configure supervisord
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf", "-n"]
