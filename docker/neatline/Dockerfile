FROM debian:bookworm

# Install dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        wget \
        unzip \
        nano \
        nginx \
        php-fpm \
        php-mysql \
        php-xml \
        php-curl \
        php-gd \
        php-mbstring \
        php-zip \
        php-bcmath \
        php-imagick \
        imagemagick \
        mariadb-client \
        ca-certificates && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Download and extract Omeka S
WORKDIR /var/www
RUN wget https://github.com/omeka/omeka-s/releases/download/v4.1.1/omeka-s-4.1.1.zip && \
    unzip omeka-s-4.1.1.zip && \
    rm omeka-s-4.1.1.zip && \
    mv omeka-s/* ./html/ && \
    rm -rf omeka-s

WORKDIR /var/www/html

# Set permissions (basic for dev, consider refining for prod)
RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

# Configure Nginx
COPY nginx.conf /etc/nginx/sites-available/default

# Expose port 80
EXPOSE 80

# Start Nginx and PHP-FPM
CMD ["sh", "-c", "php-fpm8.2 -D && nginx -g 'daemon off;'"]
