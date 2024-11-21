# Use the fauria/lamp base image
FROM fauria/lamp
MAINTAINER Ivan Diaz <ivan@opensupports.com>

# Update the package list and install necessary dependencies
RUN apt-get update && \
    apt-get install -y \
    zip unzip \
    php7.4 php7.4-zip php7.4-mbstring php7.4-mysql php7.4-xml curl ruby-full && \
    apt-get remove --yes php7.0-snmp && \
    (curl -s https://getcomposer.org/installer | php) && \
    mv composer.phar /usr/local/bin/composer && \
    gem install bundler -v 2.3.27

# Set environment variables
ENV MYSQL_HOST opensupports-db
ENV MYSQL_PORT 3306
ENV IS_DOCKER 1

# Clean up unnecessary files to reduce image size
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*
