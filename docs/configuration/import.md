---
title: Import Rules
parent: Server Configuration
layout: default
nav_order: 6
---

# Import Rules from Moroz
If you are migrating to Sleigh from a Moroz server, you likely want to import the rules rather than recreating them all.  Sleigh has a built-in function to import rules from Moroz .toml files from an HTTP URL.  Note that the rules will be imported to the default profile within Sleigh.

To import, execute this command within the Sleigh container:

`python manage.py import_toml_rules https://example.com/path/to/rules.toml`
