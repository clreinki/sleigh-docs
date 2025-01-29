---
title: Environment Variables Reference
parent: Server Configuration
layout: default
nav_order: 5
---

# Environment Variables
Most of Sleigh's settings are defined via environment variables set on your hosting platform.  Below is the list of all available options:

| Key                  | Value Type | Required | Description                                                                                  |
|----------------------|------------|----------|----------------------------------------------------------------------------------------------|
| CACHETYPE            | string     | no       | Options: (blank), 'DB', or 'REDIS'                                                           |
| DATABASE_URL         | string     | yes      | Connection string to your Postgres DB. If using Dokku, this is automatically set.            |
| DJANGO_ALLOWED_HOSTS | string     | yes      | DNS name for your Sleigh instance                                                            |
| ELASTIC_LINK         | string     | no       | URL to your 3rd party logging server's web interface                                         |
| ELASTIC_URL          | string     | no       | URL to your 3rd party logging server's listening agent, sending JSON data via HTTP post      |
| EMAIL_HOST           | string     | no       | DNS name of your SMTP server                                                                 |
| EMAIL_PORT           | integer    | no       | Port for SMTP communication                                                                  |
| EMAIL_HOST_USER      | string     | no       | Username for sending email account                                                           |
| EMAIL_HOST_PASSWORD  | string     | no       | Password for sending email account                                                           |
| EMAIL_USE_TLS        | bool       | no       | Whether to connect via TLS with SMTP server, defaults to false                               |
| DEFAULT_FROM_EMAIL   | string     | no       | Email address to use in the From: header                                                     |
| ORG                  | string     | no       | Name of your organization, display on login screen                                           |
| REDIS_URL            | string     | no       | Connection string to your Redis server. If using Dokku, this is automatically set.           |
| SECRET_KEY           | string     | no       | For best security, you should put in your own but will use pre-generated (public) key if not |
| SENTRY_DSN           | string     | no       | Your API key for Sentry.io to collect logs, errors, and performance data                     |
