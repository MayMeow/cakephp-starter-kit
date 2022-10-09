# CakePHP Application starter kit

Starter kit contains:

- Docker (Linux) or Docker Desktop (Mac or Windows)
- CakePHP 4.4.1 application skeleton
- Bootstrap 5.0 based theme plugin [WIP]
- Predefined Development docker environment (CkePHP, PostgreSQL, Redis)
- Ready to production deployment docker configuration (CakePHP, NGiNX, PostgreSQL, Redis), you can also enable traefik as well.

## Your dev environment

Services contained for dev environment in `docker-compose.dev.yml`

|Service|Ports|Description|
|----|----|----|
|Your App|8080|Your application|
|Adminer|8081|Database management tool|
|Postgres|5432 not exposed in production environment|Database server|
|Redis|6379 not exposed in production environment|Cache server|
|Minio| 9000 (Api), 9001 (Console)|S3 compatible storage server|

## Installation

There are more different ways how to use this project as template for your new application. You can use script **recomended** to 
download template for you

```bash
curl https://raw.githubusercontent.com/MayMeow/cakephp-starter-kit/main/create -o create-app
chmod +x create-app
sudo mv create-app /usr/local/bin/
```

then you can use `create-app <your-app-name>` to create your application.

 or You can clone this project

```bash
git clone --depth=1 --branch=main https://github.com/MayMeow/cakephp-starter-kit.git app_name
cd app_name
rm -rf .git # then initialize new git repository with git init and set your remotes
```

or with composer

```bash
composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-main app_name
cd app_name
```

or with Docker

```bash
mdkir app_name
cd app_name
docker run --rm --volume $(pwd):/app ghcr.io/maymeow/php-ci-cd/php-ci-cd:8.0.2-cs-git sh -c "composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-main /app"
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

## Support

In case you wan to support development you can use funding button in right panel of this project. Or if you want to help develop this project write me email (address you can find on my profile) and I create account for you on my GitLab instance.

## License

MIT
