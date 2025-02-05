---
title: Getting Started
parent: Deployment
layout: default
nav_order: 1
---

## Overview
The first step when deploying Sleigh is to choose your hosting solution. The two big considerations are:
1. whether to host in the cloud or locally
2. whether caching is desired.

Dokku is the recommended platform, as it allows you complete control over the port(s) used for communication, the number of web workers, and more flexibility with server configuration.  For caching, Sleigh supports using database-level caching - this is great for smaller deployments (<1000 devices) but adding Redis caching speeds things up and uses less CPU cycles hitting the database.

## Supported Platforms

### 1. **Dokku (Preferred)**
- **Overview**: Dokku is a Platform-as-a-Service (PaaS) solution that simplifies creating the necessary Docker containers to power Sleigh.
  - Offers the most flexibility.
  - Can run on any Ubuntu or Debian Linux server.
  - Suitable for servers with moderate specifications.
  - Dokku allows easy Redis integration

### 2. **Heroku**
- **Overview**: A popular PaaS platform that simplifies app deployment and scaling.
  - Fairly expensive but simple to deploy
  - Redis support is available but incurs additional fees.
  - Database caching can be used as an alternative.

### 3. **DigitalOcean**
- **Overview**: A cloud infrastructure provider that supports app hosting through droplets and managed services.
  - DigitalOcean is cheaper than Heroku but not free.
  - Redis support is available but comes with added costs.
  - Database caching used by default

---
For more information on deployment and configuration, consult the platform-specific guides.
