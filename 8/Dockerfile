ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

ENV NGINX_VHOST_PRESET drupal8

ARG COPY_FROM
COPY --chown=wodby:wodby ${COPY_FROM} /var/www/html

ARG DOCROOT_SUBDIR
ARG DRUPAL_SITE

RUN make init -f /usr/local/bin/actions.mk
