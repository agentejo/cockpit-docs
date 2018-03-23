uid: pid-57cc84c1a002f
type: documentation/page
created: 2016-09-04 20:32:01
modified: 2017-12-20 20:32:01
title: Fieldtypes
sort: 1

===

In Cockpit you can build custom content models defined by a collection of different field types.


### Asset
---
An asset field can reference an asset (e.g. file or pdf) you've uploaded in Cockpits Asset-Manager.


### Boolean
---
A boolean field for _true_ and _false_ values.

_Options_

```json
{
    "label": false
    "cls": "" // custom class
}
```

### Code
---
Provides a code editor field.


_Options_

```json
{
    "syntax": "text",
    "height": "auto"
}
```

### Collection-Link
---
Link other collection items.


_Options_

```json
{
    "link": "collectionname",
    "display": "fieldname",
    "multiple": false,
    "limit": false
}
```

### Color
---
Provides a color chooser field (based on Spectrum.js).


_Options_

```json
{
    "spectrum": {/* spectrum settings */}
}
```

### Date
---
Provides a date chooser field (based on Spectrum.js).

_Options_

```json
{
    "weekstart": 0,
    "format": "YYYY-MM-DD"
}
```

### File
---
Provides a file chooser field (using Cockpits built-in finder module).


### Gallery
---
Manage images and additional meta information for each image.


_Options_

```json
{
    "meta": {
        "title": {
            "type": "text",
            "label": "Title"
        }
    }
}
```

### Html
---
Html editor field with preview.

_Options_

```json
{
    "iframe"         : false,
    "mode"           : "split",
    "markdown"       : false,
    "enablescripts"  : false,
    "height"         : 500,
    "maxsplitsize"   : 1000,
    "codemirror"     : { /* codemirror settings */ },
    "toolbar"        : [ "bold", "italic", "strike", "link", "image", "blockquote", "listUl", "listOl" ],
    "lblPreview"     : "Preview",
    "lblCodeview"    : "HTML",
    "lblMarkedview"  : "Markdown"
}
```


### Image
---
Choose an image and manage additional meta information.

_Options_

```json
{
    "meta": {
        "title": {
            "type": "text",
            "label": "Title"
        }
    }
}
```


### Location
---
Location chooser to get lat,lng values.

_Options_

```json
{
    "zoomlevel": 13
}
```


### Markdown
---
Markdown editor field with preview.

_Options_

```json
{
    "height": 500
}
```

### Multipleselect
---
Select multiple values from a pre-defined list of options.

_Options_

```json
{
    "options": "Option 1, Option 2, Option 3"
}
```

### Object
---
JSON object editor.

_Options_

```json
{
    "height": 300,
    "cls": ""
}
```

### Password
---
Password field.

_Options_

```json
{
    "cls": ""
}
```

### Rating
---
Rating field.

_Options_

```json
{
    "mininmum": 0,
    "maximum": 5,
    "precision": 0
}
```


### Repeater
---
Manage multiple values of fields.

_Options_

```json
{
    "field": {"type": "text", "label": "Name"},
    "display": null // display value on re-order
}
```

or add field chooser

```json
{
    "fields": [
        {"type": "text", "label": "Name"},
        {"type": "html", "label": "Html Code"}
    ]
}
```

### Select
---
Provides a selectbox.

_Options_

```json
{
    "options": "Option 1, Option 2, Option 3"
}
```


### Set
---
Provides a field group.

_Options_

```json
{
    "fields": [
        {"name":"name", "type": "text"},
        {"name":"about", "type": "html"}
    ]
}
```

### Tags
---
Manage a list of tags.

_Options_

```json
{
    "autocomplete": []
}
```

### Text
---
Simple text input.

_Options_

```
{
  "cls": "",
  "maxlength": null, 
  "minlength": null, 
  "step": null, 
  "placeholder": null, 
  "pattern": null, 
  "size": null,
  "slug": true
}
```

### Textarea
---
Simple textarea field.

_Options_

```
{
  "cls": "",
  "maxlength": null, 
  "minlength": null, 
  "cols": null, 
  "placeholder": null, 
  "rows": null
}
```

### Time
---
Time picker field.

_Options_

```
{
  "cls": ""
}
```

### WYSIWYG
---
A WYSIWYG editor field.


_Options_

```
{
  "cls": "",
  "editor": { /* tinyMCE settings */ }
}
```
