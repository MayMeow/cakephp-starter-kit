---
title: ""
date: 2023-01-15T16:11:59+01:00
draft: false
---

## Why this project exists?

To speedup application creation. It alread have preconfigured docker development environment which include:


- Docker (Linux) or Docker Desktop (Mac or Windows)
- CakePHP 4 application skeleton
- Predefined Development docker environment (CkePHP, PostgreSQL, Redis)
- Ready to production deployment docker configuration (CakePHP, NGiNX, PostgreSQL, Redis), you can also enable traefik as well.

## Installation

```bash
composer create-project --prefer-dist maymeow/cakephp-starter-kit:dev-main app_name
cd app_name
```

For another methods check project's [Readme](https://github.com/MayMeow/cakephp-starter-kit/blob/main/README.md) file.