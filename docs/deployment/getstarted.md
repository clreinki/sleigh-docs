---
title: Getting Started
parent: Deployment
layout: default
nav_order: 1
---

## Overview
The first step when deploying Sleigh is to choose your hosting solution. The two big considerations are:
1. whether to host in the cloud or locally
2. how much fine tuning you want to do

Heroku is the easiest deployment option and is deployable in two clicks.  However if you want the most flexibility for fine tuning the performance, self hosting with Dokku would be the way to go.

## Supported Platforms

### 1. **Dokku (Self-Hosted)**
- **Overview**: Dokku is a Platform-as-a-Service (PaaS) solution that simplifies creating the necessary Docker containers to power Sleigh.
  - Offers the most flexibility.
  - Can run on any Ubuntu or Debian Linux server.
  - Suitable for servers with moderate specifications.
  - Dokku integrates Django, PostgreSQL, Redis, Nginx, and LetsEncrypt in a single stack

### 2. **Heroku (Preferred)**
- **Overview**: A popular PaaS platform that simplifies app deployment and scaling.
  - Two click deployment
  - Redis support out of the box
  - Starts at $37/mo

### 3. **DigitalOcean**
- **Overview**: A cloud infrastructure provider that supports app hosting through droplets and managed services.
  - DigitalOcean is cheaper than Heroku but not free.
  - Redis is available but comes with additional cost and config.
  - Starts at $17/mo

---
For more information on deployment and configuration, consult the platform-specific guides.
