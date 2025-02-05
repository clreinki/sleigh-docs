---
title: Deploy with Digital Ocean
parent: Deployment
layout: default
nav_order: 4
---

# Step-by-Step Guide for Digital Ocean
This guide will show you how to get up and going with Sleigh quickly by hosting on Digital Ocean (for as little as $17/mo).

## Basic Setup
- Click the below link to the prebuilt Digital Ocean template:

[![Deploy to DO](https://www.deploytodo.com/do-btn-blue-ghost.svg)](https://cloud.digitalocean.com/apps/new?repo=https://github.com/clreinki/sleigh/tree/main&refcode=fd652045edeb)

- Click Next on the Resources screen
- On Environment Variables screen, click edit and add a key DJANGO_ALLOWED_HOSTS and put in your desired domain name.  Click Next.
- On Info screen, you may update your region then click Next.
- Click Create Resources
- Wait for the first-time build process to complete (~5 minutes)
- Once the build is completed, switch to the Console tab and run the following code to initialize the database:
`python manage.py migrate && python manage.py createcachetable`
- To configure your domain, go back to the Settings tab and click Edit under the Domain header.  Follow the directions to configure DNS for your own custom domain.

At this point, you have a fully functional Sleigh instance up and running.  This instance comes with everything you need for testing or to run a small production environment.  If this is sufficient for you, you can proceed to [using Sleigh](/docs/usingsleigh/).  For a more production-ready setup, continue below for some additional configuration options.

## Additional Configuration Options
Specific to Digital Ocean, here are some additional things you may want to setup:

### Upgrade to Production DB
The PostgresDB instance in the above setup is capped at 1GB of data. While good for testing, you'll want to have a production database if you have lots of clients.  To upgrade your DB:
- Under Settings, go to the sleigh-db component
- Click Upgrade to a Managed Database, choose a node plan (10GB disk should be plenty), and click Upgrade Database

### Set Up Web Server for Static Content
By default, Python's Gunicorn web server is serving the site contents.  However static files are much more efficiently served via a standard web server.  We can do this by adding a free static site component.
- Under Settings, make sure the App component is selected.
- At the top, click Create and choose Create Resources from Source Code
- Due to a Digital Ocean limitation, you will need to fork the Sleigh repo on Github into your own account, then link your Github account.
- Once linked, select your forked Sleigh repo and click Next
- Click Edit next to the web service
- Click Edit next to resource type and change Type to Static Site and Save
- Click Edit next to Output Directory, set it to `staticfiles` and click Save
- Click Edit next to HTTP Request Routes, set it to `/static` and click Save
- Click Back, then Next, Next again, and Create Resources

After about two minutes, the build will complete and your static files will now be served from a standard web server and lessen the burden on the Sleigh process.

### Add Redis for Caching
To speed things up even more, you can utilize Redis caching. To add Redis:
- Click on Databases in the left nav bar
- Click Create Database Cluster
- Choose the same database region and select Caching for the database engine
- For the plan, choose the least expensive option
- For the name, name it `sleigh-redis` and click Create
- While waiting for it to create, follow the Getting Started prompts at the top
- For Secure this database cluster, choose your Sleigh app to give it permission
- For Eviction policy, set it to allkeys-lru as recommended
- Next thru the rest of the getting started
- Now navigate back to your Sleigh app (under App Platform)
- Under the Settings tab, click on sleigh-python
- Under Environment Variables, add a key `REDIS_URL` and value `${sleigh-redis.REDIS_URL}`
- Update the `CACHETYPE` key to have a value of `REDIS` and click Save

The app will rebuild and deploy with the new environment variables.

## Next Steps
To complete the rest of the general setup steps, please continue with the [server configuration](/docs/configuration/) section.