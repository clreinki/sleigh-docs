---
title: Email Settings
parent: Server Configuration
layout: default
nav_order: 2
---

# Email Settings (optional)
Sleigh does not have email alerts or other notifications sent via email.  The one exception is password reset emails for users who forgot their password.  For small environments with only a couple users, this likely won't be needed.  However for larger environments, you may want to configure the SMTP settings to allow for password resets to be sent.

To configure the SMTP settings, please configure the following environment variables:
- **EMAIL_HOST**
- **EMAIL_PORT**
- **EMAIL_HOST_USER**
- **EMAIL_HOST_PASSWORD**
- **EMAIL_USE_TLS**
- **DEFAULT_FROM_EMAIL**

For additional information, please see the environment variable [reference table](/docs/deployment/reference.html)