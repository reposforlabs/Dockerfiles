# Use the official Ubuntu image as the base
FROM ubuntu:20.04

# Set environment variables to avoid interactive prompts during installation
ENV DEBIAN_FRONTEND=noninteractive

# Update the package repository and install necessary packages
RUN apt-get update && apt-get install -y \
    nginx \
    mysql-server \
    php-fpm \
    php-mysql \
    php-common \
    php-gd \
    php-cli \
    php-curl \
    php-json \
    php-zip \
    php-mbstring \
    php-xmlrpc \
    php-xml \
    php-bcmath \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Configure PHP-FPM
RUN sed -i 's/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/' /etc/php/7.4/fpm/php.ini

# Start services
CMD service mysql start && service php7.4-fpm start && nginx -g 'daemon off;'

# Expose ports
EXPOSE 80

# Create a directory for the Nginx site configuration
RUN mkdir -p /var/www/html

# Copy a sample Nginx site configuration file
COPY default.conf /etc/nginx/sites-available/default

# Create a symbolic link to enable the site configuration
RUN ln -s /etc/nginx/sites-available/default /etc/nginx/sites-enabled/

# Remove the default Nginx index.html file
RUN rm /var/www/html/index.nginx-debian.html
