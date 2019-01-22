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

Imports data from a folder. It expects the structure of a `cp export` result.

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

Create language file for the admin ui in `config/i18n`.

_Arguments_

`--lang`: target language
