uid:
type: documentation/page
created: 2018-03-22 22:17:26
modified: 2016-03-22 22:17:26
title: Docker
sort: 2

===

You can set up Cockpit with Docker by grabbing the [most recent image](https://hub.docker.com/r/agentejo/cockpit/) from Docker-Hub.

## Basic Usage

---

Create your container by running

```json
docker run -d --name cockpit -p 8080:80 agentejo/cockpit
```

To complete the setup, open `http://localhost:8080/install` and follow the instructions there.

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
To do this, you’ll need to set up some environment variables in your container as well as include a custom `config.php` file that picks up these variables. 

Workinge example custom config.php file that picks up environment variables from your container:

```
<?php


$configs = [];

if (!empty(getenv('COCKPIT_SESSION_NAME'))){
  $configs['session.name'] = getenv('COCKPIT_SESSION_NAME');
}

if (!empty(getenv('COCKPIT_SALT'))){
  $configs['sec-key'] = getenv('COCKPIT_SALT');
}

if (!empty(getenv('COCKPIT_I18N'))){
  $configs['i18n'] = getenv('COCKPIT_I18N');
}

if (!empty(getenv('COCKPIT_DATABASE_SERVER'))){
  $configs['database'] = [
    "server"  => getenv('COCKPIT_DATABASE_SERVER'),
    "options" => ["db" => getenv('COCKPIT_DATABASE_NAME')]
  ];
}

if (!empty(getenv('COCKPIT_MAILER_FROM'))){
  $configs['mailer'] = [
      "from"      => getenv('COCKPIT_MAILER_FROM'),
      "transport" => getenv('COCKPIT_MAILER_TRANSPORT'),
      "host"      => getenv('COCKPIT_MAILER_HOST'),
      "user"      => getenv('COCKPIT_MAILER_USER'),
      "password"  => getenv('COCKPIT_MAILER_PASSWORD'),
      "port"      => getenv('COCKPIT_MAILER_PORT'),
      "auth"      => getenv('COCKPIT_MAILER_AUTH'),
      "encryption"=> getenv('COCKPIT_MAILER_ENCRYPTION')
  ];
}
return $configs;
```

Docker environment variables:

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

To link your MongoDB container to your cockpit instance, configure your volumes accordingly, and make sure you link your containers over a network:

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
