FROM php:7.4-cli

LABEL \
   Maintainer="TYPO3 Core Team" \
   Description="This image provides a Php CLI Manager for generating TYPO3 Fluid view helper schema." \
   Vendor="typo3"

# Install Composer prerequisites
RUN apt-get -q --no-allow-insecure-repositories update \
   && apt-get install --assume-yes --no-install-recommends \
         git \
         unzip \
         libzip-dev \
   && docker-php-ext-install \
         zip \
   && rm -rf /var/lib/apt/lists/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer \
   | php -- --version="2.2.4" --install-dir=/usr/bin --filename=composer

# Smoke test
RUN php --version \
   && composer --version \
   && git --version

WORKDIR /fluid-schema-generator
ENTRYPOINT [""]