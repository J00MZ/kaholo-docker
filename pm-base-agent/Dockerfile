# Run on Ubuntu 16.04
FROM ubuntu:22.04

# Install system dependencies
RUN apt-get update
RUN apt-get install -y git python build-essential curl mongodb supervisor
RUN curl -sL https://deb.nodesource.com/setup_6.x | bash - 
RUN apt-get install -y nodejs
RUN mkdir -p /var/www
RUN mkdir -p /var/log/supervisor


# Install base agent for localhost
RUN git clone https://github.com/ProductionMap/production-map-base-agent.git /var/www/production-map-base-agent
WORKDIR /var/www/production-map-base-agent/production-map-base-agent
RUN npm install
COPY ./baseagent.js conf/baseagent.js

# Configure supervisord
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

CMD ["/usr/bin/supervisord", "-c", "/etc/supervisor/conf.d/supervisord.conf", "-n"]
