ARG WODBY_BASE_IMAGE
FROM ${WODBY_BASE_IMAGE}

ARG COPY_FROM
COPY ${COPY_FROM} /var/www/html

ARG DOCROOT_SUBDIR
ARG DRUPAL_SITE

ENV FILES_DIR /mnt/files
ENV APP_ROOT /var/www/html

RUN set -ex; \
    \
    drupal_root=""; \
    if [[ -n "${DOCROOT_SUBDIR}" ]]; then \
      drupal_root="${APP_ROOT}/${DOCROOT_SUBDIR}"; \
    else \
      drupal_root="${APP_ROOT}"; \
    fi; \
    \
    drupal_site_dir="${drupal_root}/sites/${DRUPAL_SITE}"; \
    mkdir -p "${drupal_site_dir}"; \
    app_public_dir="${drupal_site_dir}/files"; \
    \
    if [[ -d "${app_public_dir}" ]]; then \
        if [[ ! -L "${app_public_dir}" ]]; then \
            if [[ "$(ls -A "${app_public_dir}")" ]]; then \
                echo "Error: failed to symlink public storage directory to a persistent volume"; \
                echo "Directory ${app_public_dir} either must be empty or cannot exist"; \
                echo "(use files import to migrate existing public files)"; \
                exit 1; \
            # If dir is not symlink and empty, remove it and link. 
            else \
                echo "Empty public storage dir detected: removing and symlinking"; \
                rm -rf "${app_public_dir}"; \
                ln -sf "${FILES_DIR}/public" "${app_public_dir}"; \
            fi \
        else \
            echo "Symlink already in place"; \
        fi \
    else \
        echo "No public storage dir detected: just symlinking"; \
        ln -sf "${FILES_DIR}/public" "${app_public_dir}"; \
    fi
