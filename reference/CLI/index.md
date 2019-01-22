type: documentation/page
title: CLI
sort: 5

===

Cockpit comes with a CLI containing useful commands to interract from the command line.


### List of command:

#### `cp export`
Export all data from cockpit to a directory

Arguments:
```--target```: The destination directory for the export of the cockpit data

Possible subcommands to export only certain types of data:
`export/accounts`, `export/assets`, `export/tmp`, `export/collections`, `export/singletons`, `export/forms`

#### `cp flush`
Deletes all the data in cockpit (from the db)

Possible subcommands to flush only certain types of data:
`flush/accounts`, `flush/assets`, `flush/tmp`, `flush/collections`, `flush/singletons`, `flush/forms`

#### `cp import`
Imports data from a folder. It expects the structure of a `cp export`

Arguments:
```--src```: the source folder containing the cockpit data to import

Possible subcommands to import only certain types of data:
`import/accounts`, `import/assets`, `import/tmp`, `import/collections`, `import/singletons`, `import/forms`
