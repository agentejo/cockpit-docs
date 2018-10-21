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

# cockpit default language
i18n: de

# define the languages you want to manage
languages:
    fr: French
    de: German

# define allowed file types for uploads (global)
allowed_uploads: pdf, png, jpg, jpeg, svg, gif

# define additional groups
groups:
    author:
        $admin: false
        $vars:
            finder.path: /storage/upload
            media.path : /storage/media
            finder.allowed_uploads: png, jpg, jpeg
            assets.allowed_uploads: png, jpg, jpeg
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
    from_name : John Doe
    transport : smtp
    host      : smtp.myhost.tld
    user      : username
    password  : xxpasswordxx
    port      : 25
    auth      : true
    encryption: ssl # '', ssl, tls or starttls
    reply_to  : john.doe@mydomain.tld
    cc        :
        - mail1@example.com
        - mail2@example.com
    bcc       :
        - mail1@example.com
        - mail2@example.com

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
 
