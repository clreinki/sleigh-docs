---
title: ElasticSearch Integration
parent: Server Configuration
layout: default
nav_order: 3
---

# ElasticSearch Integration (optional)
By default, Sleigh stores all Santa client events in its database.  However for large environments, you may want use Logstash/Elasticsearch or another 3rd party log aggregation tool as the amounts of events can become hard to sort thru.  

To configure the 3rd party logging, please configure the following environment variables:
- **ELASTIC_URL** = The URL for your logging server
- **ELASTIC_LINK** = On the reporting page, a button will appear with this URL for you to access your separate reporting server

By configuring these two environment variables, you can replace Sleigh's built-in logging with your own.

For additional information, please see the environment variable [reference table](/docs/deployment/reference.html)