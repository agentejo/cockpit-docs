uid: pid-57cdeef64447c
type: documentation/page
created: 2016-09-05 22:17:26
modified: 2016-09-05 22:17:26
title: Configuration
sort: 0

===

By default, Cockpit doesn't need any further configuration to run. However, you might want to manage multi-language content or use MongoDB instead of SQLite as your favorite data storage. Therefore Cockpit provides an easy way to tweak some settings.



To do so, go to _Settings > System Settings_ and configure Cockpit via YAML.


### Possible settings:

```yaml

# cockpit session name
app.name: My Project X

# cockpit session name
session.name: mysession

# define the languages you want to manage
languages:
    fr: French
    de: German

# define additional groups
groups:
    author:
        $admin: false
        $vars:
            finder.path: /storage/upload
        cockpit:
            backend: true
            finder: true
        collections:
            manage: true

# use mongodb as main data storage
database:    
    server: mongodb://localhost:27017
    options:
        db: cockpitdb


# use smtp to send emails
mailer:
    from      : info@mydomain.tld
    transport : smtp
    host      : smtp.myhost.tld
    user      : username
    password  : xxpasswordxx,
    port      : 25,
    auth      : true,
    encryption: '' # '', 'ssl' or 'tls'

```

### Group ACLs

Access to cockpit is managed by a simple access control list (ACL). The ACLs can be defined by module and acl name in the settings above. The following ACLs can be defined on a per-group basis:

  * `cockpit`: Access to the cockpit itself
    * `backend`: Access to the admin backend - you need this in order to log in etc.
    * `finder`: Access to the media finder
  * `collections`: Special ACLs for collections
    * `manage`: Manger rights for collections. You need this for certain AJAX requests.
 