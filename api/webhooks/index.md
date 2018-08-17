uid: pid-57cd7de46c809
type: documentation/page
created: 2016-09-05 14:15:00
modified: 2016-09-05 14:15:00
title: Webhooks
sort: 5

===

A webhook is a user-defined HTTP callback. It is a mechanism that sends real-time information to any third-party app or service.

Webhooks allow you to specify a URL to which you would like Cockpit to post data when an event happens. So, for instance, if you wish to be notified every time a new collection entry is created, you can create a webhook for it. Webhooks can be created for almost all events in Cockpit.


### Create a webhook

![Create a webhook](create.png)


### Advanced options

![Advanced Options](advanced.png)

All data will be send as _application/json_.


### Useful events

- _collections.save.after_
- _collections.remove.after_
- _regions.update_
- _regions.remove_