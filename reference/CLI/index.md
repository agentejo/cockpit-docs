type: documentation/page
title: CLI
sort: 5

===

Cockpit comes with a CLI containing useful commands to interract from the command line.


## List of commands:

### ./cp export

Export all data from cockpit to a directory

_Arguments_

`--target`: The destination directory for the export of the cockpit data

Possible subcommands to export only certain types of data:

- `./cp export/accounts`
- `./cp export/assets`
- `./cp export/tmp`
- `./cp export/collections`
- `./cp export/singletons`
- `./cp export/forms`

### ./cp import

Imports data from a folder. **It expects the structure of a `cp export` result**.

_Arguments_

`--src`: the source folder containing the cockpit data to import

Possible subcommands to import only certain types of data:

 - `./cp import/accounts`
 - `./cp import/assets`
 - `./cp import/tmp`
 - `./cp import/collections`
 - `./cp import/singletons`
 - `./cp import/forms`


### ./cp flush

Deletes all the data in cockpit (from the db)

Possible subcommands to flush only certain types of data:

- `./cp flush/accounts`
- `./cp flush/assets`
- `./cp flush/tmp`
- `./cp flush/collections`
- `./cp flush/singletons`
- `./cp flush/forms`


### ./cp create-lang

Create language file for the admin ui in `config/cockpit/i18n`.

_Arguments_

`--lang`: target language

### ./cp install/addon

Pulls addon zip packager from url or github repo name. 

_Arguments_
`--url`: url 
`--name`: repository name belonging to agentejo organization on github

For _example_ if we wanted to download Lokalize addon from github we would need to run following command:
```
./cp install/addon --name Lokalize
```

### ./cp account/create

Creates new Cockpit user

_Arguments_
`--user`: username
`--email`: email
`--passwd`: plain password


### ./cp account/generate-password

Encodes provided password and returns its hash.

_Arguments_
`--passwd`: plain password

### ./cp jobs/start-runner

Starts job runner for given task id.

_Arguments_
`idle`: task id

### ./cp jobs/stop-runner

Stops job runner

### ./cp removefield/collections

Deletes field from given collection. Note that this does not clean removed field's data from entries.

_Arguments_
`--collection`: target collection
`--field`: field to be removed

### ./cp rename/collections

Renames collection.

_Arguments_
`--name`: target collection
`--to`: new collection name

### ./cp renamefield/collections

Renames field in given collection.

_Arguments_
`--collection`: target collection
`--field`: target field
`--newfield`: new field name