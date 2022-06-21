FROM ghcr.io/maymeow/php-ci-cd/php-ci-cd:8.1.6-cs-git-psalm AS build-env

WORKDIR /app

COPY . /app

## uncomment --no-scripts if you want to remove composer postinstallation scripts
RUN composer install --no-ansi --no-dev --no-interaction --no-plugins --no-progress --optimize-autoloader #--no-scripts

FROM ghcr.io/maymeow/webapp-base/webapp-base:8.1.6

ARG user=www-data

COPY --from=build-env /app /var/www

RUN chown -R $user:$user /var/www

WORKDIR /var/www

RUN chmod -R 777 /var/www/logs

USER $user
