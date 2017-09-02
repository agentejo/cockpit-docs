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

# use mongodb as main data storage
database:    
    server: mongodb://localhost:27017
    options:
        db: cockpitdb
```
