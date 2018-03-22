uid:
type: documentation/page
created: 2018-03-22 22:17:26
modified: 2016-03-22 22:17:26
title: Docker
sort: 2

===

You can set up Cockpit with Docker by grabbing the [most recent image](https://hub.docker.com/r/agentejo/cockpit/) from Docker-Hub.

## Basic Usage

--

Create your container by running

```json
docker run -d --name cockpit -p 8080:80 agentejo/cockpit
```

Next, follow the [setup instructions](https://getcockpit.com/documentation/getting-started/installation)

## Extend the Image

You can extend this image and add your custom cockpit/custom/config.php

```json
FROM agentejo/cockpit
COPY config.php /var/www/html/custom/config.php
```

## Docker Compose

---

### MongoDB

For larger projects you may find you want to use mongoDB over the built-in SQLite.
To do this, you’ll need to set up some environment variables in your container:

```json
services:
    cms:
        image: agentejo/cockpit
        environment:
            COCKPIT_SESSION_NAME: cockpit
            COCKPIT_SALT: _create_your_own_
            COCKPIT_DATABASE_SERVER: 'mongodb://db:27017'
            COCKPIT_DATABASE_NAME: cockpit_master
```

**Quicktip:** generate your `COCKPIT_SALT` by typing `uuidgen` into your terminal.

To link your mongoDB container to your cockpit instance, configure your volumes accordingly, and make sure you link your containers over a network:

```json
services:
    db:
        image: 'mongo:latest'
        volumes:
        - 'mongo-vol:/data/db'
        networks:
        - yournetwork
    cms:
        image: agentejo/cockpit
        environment:
            COCKPIT_SESSION_NAME: cockpit
            COCKPIT_SALT: _create_your_own_
            COCKPIT_DATABASE_SERVER: 'mongodb://db:27017'
            COCKPIT_DATABASE_NAME: cockpit_master
        depends_on:
        - db
        ports:
        - "8080:80"
        networks:
        - yournetwork
    networks:
    yournetwork:
        driver: bridge
    volumes:
    mongo-vol: null
```
