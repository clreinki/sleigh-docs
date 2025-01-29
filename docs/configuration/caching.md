---
title: Caching Options
parent: Server Configuration
layout: default
nav_order: 1
---

# Caching Options (Recommended)
You have a few options when it comes to how to utilize caching.  Redis is the recommended option.

## No Caching
This is the default configuration of Sleigh and is perfectly fine for small deployments.  In this situation, each Santa client checkin dynamically calculates the rules for the client.  There is no additional configuration needed.

## Database Caching
With database caching, Sleigh will saved the calculated rules for each client in the database.  This means each client will only need calculated once and the calculated result will be stored in the database.  Database caching allows for better performance without increasing the cost or complexity of having a Redis instance.

To enable database caching:
- Set the CACHETYPE environment variable to 'DB'
- Run manage.py with the createcachetable argument

Script for Dokku:

```
# Set CACHETYPE environment variable to DB
dokku config:set sleigh CACHETYPE='DB'

# Trigger creation of cache table in DB
dokku run sleigh python manage.py createcachetable
```

## Redis Caching
Redis is the preferred caching method.  When a client's configuration is calculated, it is saved in-memory via Redis.  This allows for fastest response time as no database queries are required to retrieve Santa configurations.

To enable Redis caching:
- Set the CACHETYPE environment variable to 'REDIS'
- Set the REDIS_URL environment variable with your Redis connection string

Script for Dokku:

```
# Install Dokku Redis plugin
sudo dokku plugin:install https://github.com/dokku/dokku-redis.git redis

# Create and link Redis instance
dokku redis:create sleigh_redis
dokku redis:link sleigh_redis sleigh --no-restart "true"

# Tell Sleigh to use Redis via an environment variable
dokku config:set sleigh CACHETYPE='REDIS'
```
