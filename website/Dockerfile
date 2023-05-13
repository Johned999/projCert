# Use the official PHP base image
FROM php:7.4-apache

# Set the working directory in the container
WORKDIR /var/www/html

# Copy all files from the root point to the container
# COPY . /var/www/
# Copy only PHP files to the container
COPY *.php /var/www/html/

# Copy the "content" directory to the container
COPY content /var/www/html/content
# Copy the "template" directory to the container
COPY template /var/www/html/template

# Install any dependencies required by your PHP application
RUN apt-get update \
    && apt-get install -y \
       libpng-dev \
       libjpeg-dev \
    && docker-php-ext-configure gd --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

#Change the permissions on all files.
RUN chown -R www-data:www-data /var/www/html

# Expose the container port
EXPOSE 80

# Start the Apache web server
CMD ["apache2-foreground"]
