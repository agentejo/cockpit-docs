uid: pid-57cdeef64447c
type: documentation/page
created: 2016-09-05 22:17:26
modified: 2016-09-05 22:17:26
title: Configuration
sort: 0

===

By default, Cockpit doesn't need any further configuration to run. However, you might want to manage multi-language content or use MongoDB instead of SQLite as your favorite data storage. Therefore Cockpit provides an easy way to tweak some settings.


To do so, create a configuration file in the config folder: `/config/config.php`.


### Possible settings:

```php
<?php

return [

    # cockpit session name
    'app.name' => 'My Project X',

    # cockpit session name
    'session.name' => 'mysession',

    # app custom security key
    'sec-key' => 'xxxxx-SiteSecKeyPleaseChangeMe-xxxxx',

    # site url (optional) - helpful if you're behind a reverse proxy
    'site_url' => 'https://mydomain.com',

    # define the languages you want to manage
    'languages' => [
        'fr' => 'French',
        'de' => 'German'
    ],

    # define additional groups
    'groups' => [
        'author' => [
            '$admin' => false,
            '$vars' => [
                'finder.path' => '/storage/upload'
            ],
            'cockpit' => [
                'backend' => true,
                'finder' => true
            ],
            'collections' => [
                'manage' => true
            ]
        ]
    ],

    # use mongodb as main data storage
    'database' => [   
        'server' => 'mongodb://localhost:27017',
        'options' => [
            'db' => 'cockpitdb'
        ]
    ],


    # use smtp to send emails
    'mailer' => [
        'from'       => 'info@mydomain.tld',
        'transport'  => 'smtp'
        'host'       => 'smtp.myhost.tld',
        'user'       => 'username'
        'password'   => 'xxpasswordxx',
        'port'       => 25,
        'auth'       => true,
        'encryption' => '' # '', 'ssl' or 'tls'
    ]

    # Define Access-Control (CORS) settings.
    # Those are the default values. You don't need to duplicate them all.
    'cors' => [
      'allowedHeaders' => 'X-Requested-With, Content-Type, Origin, Cache-Control, Pragma, Authorization, Accept, Accept-Encoding, Cockpit-Token',
      'allowedMethods' => 'PUT, POST, GET, OPTIONS, DELETE',
      'allowedOrigins' => '*',
      'maxAge' => '1000',
      'allowCredentials' => 'true',
      'exposedHeaders' => 'true',
    ],
];
```

### Group ACLs

Access to cockpit is managed by a simple access control list (ACL). The ACLs can be defined by module and acl name in the settings above. The following ACLs can be defined on a per-group basis:

* `$admin`: Give all admin rights to the group. This overwrites whatever is defined under `cockpit` (Boolean. False if omitted)
* `cockpit`: Access to the cockpit itself (Array)
    * `accounts`: Access to the cockpit accounts (Boolean. False if omitted)
    * `backend`: Access to the admin backend - you need this in order to log in etc (Boolean. False if omitted)
    * `finder`: Access to the media finder (Boolean. False if omitted)
  * `collections`: Special ACLs for collections (Array)
    * `manage`: Manger rights for collections. You need this for certain AJAX requests (Boolean. False if omitted)
* `$vars`: Overwrite variables used by cockpit (Array)
  * `finder.path`: Root path from which the finder will show the files. Only used if `cockpit.finder` is true (String. Default is /)
