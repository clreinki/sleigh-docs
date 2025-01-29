---
title: Deploy with Dokku
parent: Deployment
layout: default
nav_order: 2
---

# Step-by-Step Guide for Dokku
- [Install Dokku](https://dokku.com/docs/getting-started/installation/) on your Ubuntu or Debian server/VM (requires min 1gb RAM)
- Add your SSH key and set global domain as shown in Dokku directions
- Create your dokku app and subservices by follow the below:

```
# Create the sleigh instance (URL will be sleigh.<yourdomain>)
dokku apps:create sleigh

# Install Postgres plugin, create DB, and link to your Sleigh app
sudo dokku plugin:install https://github.com/dokku/dokku-postgres.git
dokku postgres:create sleighdb
dokku postgres:link sleighdb sleigh

# Pull code from Github and build the app
dokku git:sync --build sleigh https://github.com/clreinki/sleigh.git main
```
- [Enable SSL](https://dokku.com/docs/deployment/application-deployment/#setting-up-ssl) by importing a certificate or using LetsEncrypt:

```
# install the letsencrypt plugin
# plugin installation requires root, hence the user change
sudo dokku plugin:install https://github.com/dokku/dokku-letsencrypt.git

# set global email for letsencrypt
dokku letsencrypt:set --global email <youremail>@<yourdomain>

# set a custom domain that you own for your application
dokku domains:set sleigh sleigh.<yourdomain>

# enable letsencrypt
dokku letsencrypt:enable sleigh

# enable auto-renewal
dokku letsencrypt:cron-job --add
```
- By default, Sleigh does not use caching until the cache type is specified.  For this, we will install and configure Redis:

```
# Install Dokku Redis plugin
sudo dokku plugin:install https://github.com/dokku/dokku-redis.git redis

# Create and link Redis instance
dokku redis:create sleigh_redis
dokku redis:link sleigh_redis sleigh --no-restart "true"

# Tell Sleigh to use Redis via an environment variable
dokku config:set sleigh CACHETYPE='REDIS'
```

- Lastly, improve your security by setting the DJANGO_ALLOWED_HOSTS environment variable to your Sleigh instance's domain as well as [generate](https://djecrety.ir/) a new Django SECRET_KEY 

```
# Set both environment variables
dokku config:set sleigh DJANGO_ALLOWED_HOSTS='sleigh.<yourdomain>' SECRET_KEY='<your key>'
```
You should now have a working Sleigh instance!  To configure additional server settings, continue with [server configuration](/docs/configuration/) or skip right to [using Sleigh](/docs/usingsleigh/).