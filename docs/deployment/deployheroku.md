---
title: Deploy with Heroku
parent: Deployment
layout: default
nav_order: 3
---

# Step-by-Step Guide for Heroku
Deploying with Heroku is by far the easiest way to get up and running with Sleigh.  This guide will show you how to deploy to Heroku for around $37/mo.

To deploy:

- Click the below link to the prebuilt Heroku template:
[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://www.heroku.com/deploy?template=https://github.com/clreinki/sleigh)

- Fill in the app name, scroll to the bottom, and click Create

That's it!  Once it's deployed, you'll have a fully functional Sleigh instance ready to go with a 10GB database and 25MB of Redis caching (which you can upgrade based on your needs).

I'd recommend [configuring a custom domain](https://devcenter.heroku.com/articles/custom-domains).  To configure additional server settings, continue with [server configuration](/docs/configuration/) or skip right to [using Sleigh](/docs/usingsleigh/).