FROM drupal:php7.4-apache

RUN apt-get update; \
  apt-get install -y --no-install-recommends \
  git \
  wget \
  unzip \
  libzip-dev; \
  rm -rf /var/lib/apt/lists/*; \
  docker-php-ext-configure zip --with-libzip; \
  docker-php-ext-install zip

ENV PATH="/root/.composer/vendor/bin:$PATH"
ENV PATH="$PATH:/opt/drupal/vendor/bin"

RUN composer global require consolidation/cgr

RUN rm -rf /opt/drupal

WORKDIR /opt/drupal

RUN ln -s docroot web

WORKDIR /opt/drupal/web

RUN touch /opt/drupal/web/.x
