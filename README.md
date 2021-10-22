# CakePHP Application starter kit

Starter kit contains:

- CakePHP 4.0 application skeleton
- Bootstrap 5.0 based theme plugin [WIP]
- Predefined Development docker environment (CkePHP, PostgreSQL, Redis)
- Ready to production deployment docker configuration (CakePHP, NGiNX, PostgreSQL, Redis), you can also enable traefik as well.

## Your dev environment

Services contained for dev environment in `docker-compose.dev.yml`

|Service|Ports|Description|
|----|----|----|
|Cakephp App|8765|Your application|
|Adminer|8080|Database management tool|
|Postgres|5432 not exposed|Database server|
|Redis|6379 not exposed|Cache server|
|Minio| 9000 (Api), 9001 (Console)|S3 compatible storage server|

## Installation

There are more different ways how to use this project as template for your new application. You can clone this project

```bash
git clone --depth=1 --branch=main https://github.com/MayMeow/cakephp-starter-kit.git app_name
cd app_name
rm -rf .git # then initialize new git repository with git init and set your remotes
```

or with composer

```bash
composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-master app_name
cd app_name
```

or with Docker

```bash
mdkir app_name
cd app_name
docker run --rm --volume $(pwd):/app ghcr.io/maymeow/php-ci-cd/php-ci-cd:7.4.16-cs-1 sh -c "composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-main /app"
sudo chown -R $USER:$GID .
```

## Configuration

Application will generate security key automaticlly with each install and with each build. This is OK for development but not for production. It is recomended to generate key manually as follows

```bash
docker-compose -f docker-compose.dev.yml run --rm cake-app php bin/cake.php generate_security_key
```

When you have key copy it and update `.env.production` file and paste your key right behind `SECURITY_SALT=` without any quotes.

Next update `DB_USER`, `DB_NAME`, `DB_PASSWORD`, `POSTGRES_PASSWORD`, `POSTGRES_USER` and db `POSTGRES_DB`. Other variables are preconfigured and if you dont change values in docker compose files you are good to go.

### Enabling debug mode

For developmen you can enable debug mode by setting `DEBUG=true` in `.env.production` file. **It is strongly recomended to diasble debug mode for production environment**

## Console

To access console use command as follows

```bash
docker-compose -f docker-compose.dev.yml run --rm cake-app php bin/cake.php
```
When you need to acces redis console you can use following command:

Getting all keys from redis cacge database
```bash
docker exec -it cake_redis redis-cl

# keys *
```

## Issues, new features

If you found an issue or you want to provide feedback or you have an idea for new features. Use [Issue tab](https://github.com/MayMeow/cakephp-starter-kit/issues) on github project page.

## Development

I running development of this project on my own gitlab instace because is easier for me to setup and maintain CI pipelines. I mirroring to this repository only protected pranches for now only `main` branch. Code is tested and only after successfull pipeline is merged to tha main branch and thenis mirrored to this github repository.

If you want to see code on my own instance, project have set visibility to public so you can see source code, pipleine logs and more. Source code is here [maymeow/cakephp-starter-kit](https://git.moew.cloud/maymeow/cakephp-starter-kit)

## Support

In case you wan to support development you can use funding button in right panel of this project. Or if you want to help develop this project write me email (address you can find on my profile) and I create account for you on my GitLab instance.

## License

MIT
