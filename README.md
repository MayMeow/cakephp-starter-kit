# CakePHP Application starter kit

Starter kit contains:

- CakePHP 4.0 application skeleton
- Bootstrap 5.0 based theme plugin [WIP]
- Predefined Development docker environment (CkePHP, PostgreSQL, Redis)
- Ready to production deployment docker configuration (CakePHP, NGiNX, PostgreSQL, Redis), you can also enable traefik as well.

## Installation

```bash
git clone https://github.com/MayMeow/cakephp-starter-kit.git
```

or with composer

```bash
composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-master /app
```

or with Docker

```bash
docker run --rm --volume /home/may/Projects/cakephp-starter-kit:/app ghcr.io/maymeow/php-ci-cd/php-ci-cd:7.4.16-cs-1 sh -c "composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-master /app"
```
