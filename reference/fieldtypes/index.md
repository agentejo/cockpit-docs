uid: pid-57cc84c1a002f
type: documentation/page
created: 2016-09-04 20:32:01
modified: 2017-12-20 20:32:01
title: Fieldtypes
sort: 1

===

In Cockpit you can build custom content models defined by a collection of different field types.


### Access-List
---
Provides chooser for available Access groups


### Account-Link
---
Link one or more user accounts

_Options_

```json
{
    "multiple": false,
    "limit": null,
}
```


### Asset
---
An asset field can reference an asset (e.g. file or pdf) you've uploaded in Cockpits Asset-Manager.


### Boolean
---
A boolean field for _true_ and _false_ values.

_Options_

```json
{
    "label": false,
    "default": false,
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


### Colortag
---
Provides chooser for predefined colors

_Options_

```json
{
    "size": "inherit",
    "colors": [/* list of hex color codes */]
}
```


### Date
---
Provides a date chooser field (based on Spectrum.js).

_Options_

```json
{
    "weekstart": 0,
    "format": "YYYY-MM-DD",
    "cls": "",
    "placeholder": ""
}
```

### File
---
Provides a file chooser field (using Cockpits built-in finder module).

_Options_

```json
{
    "cls": "",
    "placeholder": "No file selected..."
}
```


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


### Layout
---

Layout editor

_Options_

```json
{
    "components": {
        /* Custom components */
    }
}
```

### Layout-Grid
---

Layout editior with preselected grid component


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
    "height": "300px",
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
    "display": null, // display value on re-order
    "limit": null
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
    "cls": "",
    "options": "Option 1, Option 2, Option 3",
    "default": "Option 2"
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
    ],
    "display": "{name} <small>{about}</small>"
}
```


### Tags
---
Manage a list of tags.

_Options_

```json
{
    "autocomplete": [],
    "placeholder": "Add Tag..."
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
  "allowtabs": true,
  "maxlength": null,
  "minlength": null,
  "placeholder": null,
  "cols": null,
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
  "rows": null,
  "editor": { /* tinyMCE settings */ }
}
```
