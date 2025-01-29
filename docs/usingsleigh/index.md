---
title: Using Sleigh
has_children: false
nav_order: 4
layout: default
back_to_top: true
back_to_top_text: "Back to top"
---

- TOC
{:toc}

## Logging in the First Time
When you navigate to your Sleigh URL, you'll be prompted to login.  **The default username/password is sleighadmin/sleighadmin - CHANGE THIS!**  Once you log in, click on your profile pic at the top right and go to Change Password.

## Set Up Additional Users
You can set up additional users under the User Management tab.  You can also delete any users that you no longer want, including the sleighadmin user if desired.

## Key Concepts with Sleigh
For anyone with experience with Santa, the general configuration should be fairly straightforward.  I will refer extensively to the Santa docs as their documentation is quite good.

The basic building blocks of Sleigh are Configs, Profiles, and Rules.

### Prerequisites
Before you begin using Sleigh, the following is assumed about your environment already:
- All [necessary MDM profiles](https://northpole.dev/deployment/getting-started.html) have been pushed to your Macs
- The SyncBaseURL in the client profile is your "https://sleigh.<yourdomain>/santa/"
- The MachineIDKey is set to the device serial number

### Configs
A config is what configures the client mode, check in times, and other general settings like shown in [Santa's mode](https://northpole.dev/concepts/mode.html) documentation.  Each sleigh instance starts with a default configuration that cannot be deleted.  Any new clients will automatically get the default config.

### Profiles
A profile is a collection of rules.  Each sleigh instances starts with a default profile that cannot be deleted.  Any new clients will automatically get the default profile.

In addition, there are two types of profiles: regular and standalone.  A regular profile **stacks** with the rules in the default profile, whereas a standalone profile **replaces** the default profile.  This gives granularity with departments that need special software.

For example, your default profile may contain basic office software but your developers may need access to additional tools.  In this case, you can create a new profile and add additional rules to allow specialized software on just those individual machines, while still getting the rules from the default profile rather than recreating them all in a standalone profile.

### Rules
Rules allow you to block/allow software via various rule types.  See [Santa's rule](https://northpole.dev/concepts/rules.html) documentation for full guidance.

### Assigning Configs/Profiles to Devices
Once you have defined your configs and profiles, you can go to the Device Inventory screen to view devices that are checking in with Sleigh.  To change a device's config/profile, check the box next to the device(s) you'd like to modify, and at the top right select the new config/profile and click Update.

{: .highlight }
If you are just rolling out Santa, the best way to do it is have the default config be in Monitor mode and create a separate Lockdown config.  This will allow all new devices that check in to be in monitor mode and you can then select a subset of devices to test on first by assigning them the new Lockdown config.

## Reporting
There are three tabs related to reporting: Device Inventory, Santa Events, and Sleigh Changelog

### Device Inventory
This is where you can change the config/profile assigned to devices.  It also allows you to see their last sync time as well as how many rules they report having.  You can also see the version of Santa installed.

### Santa Events
This is where events that happen on clients are recorded.  For events that you do not want to see in the future, you can check the box next to the event and click Ignore Selected at the top. This will hide all current **and future** events of that type from displayed.

If you are using Elasticsearch or another 3rd party log aggregator as described here, you will not see any events [here](/docs/configuration/elastic.html).  Instead you will see a link to your other system.  In addition, your home page dashboard will not show any events.

### Sleigh Changelog
All changes that an admin makes to Sleigh are logged here.