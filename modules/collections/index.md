uid: pid-57cc94a392bc4
type: documentation/page
created: 2016-09-04 21:39:47
modified: 2016-09-05 15:50:05
title: Collections
sort: 0

===

A _Collections_ is an abstraction to store structured content. A collection is defined by its _fields_ (how is the collections structured), _items_ and _permissions_ (you can find detailed documentation on permissions in the [Permissions Page](link-to-permission). One example of a collection would be a collection named _Members_, used to store members of a company.

## Create a Collection

To create a collection, either click the "plus" button or "Create a collection" from the dashboard. Alternatively, you can also created from the collections overview page.

![create a collection from the dashboard](./create-a-collection-1.png)

![create a collection from the collections list](./create-a-collection-2.png)

On the collection view, you are presented with two parts: _Collection Info_ and _Collection Fields_.

![collection detail view](./create-a-collection-3.png)

### Collection Info

Start by filling the collection info by defining:

* _Name_: the name of the collection. This should be a computer friendly name as this will be used to retrieve the collection data throught the api. For this example, we'll call it _members_.
* _Label_: (optional) human-friendly name that will appear on the Cockpit Admin UI.
* _Icon_: (optional) a pictogram to easily identify the collection on the Cockpit Admin UI.
* _Color_: (optional) a color to easily idenfity the collection on the Cockpit Admin UI.
* _Description_: (optional) a short description of what is the collection used.
* _Sortable entries_: (TODO)
* _Show in system menu_: (TODO)

### Collection Fields

The fields of a collection is the structured of the collection items. This includes what properties each item should have, validation rules for those properties, and some hints that help content editors create/edit collection items.

In this example, we'll add two fields:

* A field called _name_, of type _Text_, required.
* A field called _role_, of type _Text_, translatable.

In order to do that, click on _Add Field_, as shown in the following screenshot:

![add a field to a collection](./create-a-collection-4.png)

![add a field to a collection](./create-a-collection-5.png)

A new field will be shown on the fields. After defining a unique, computer-friendly, _field name_ on this view, you can click on the _cog_ button to further configure the field. The field details will appear in a modal.

![add a field to a collection](./create-a-collection-6.png)

Here you can define the following information:

* _Field Type_: the type of the field. Read more on what types are available on the [Field Type Page](link-to-field-type-page). In exemple we want the type to be of _Text_.
* _Field Label_: (optional) human-friendly name to appear on the Admin UI.
* _Field Info_: (optional) a short description on the field.
* _Field Group_: (optional) it's common to group fields together so that they appear groupped in one tab while inserting/editing one item.
* _Options_: (optional) a JSON object representing the field options. The available options depends on the _Field Type_. You can find a full reference of the available field type options in the [Field Type Page](link-to-field-type-page).
* _Required_: if the field is required or not (if marked as required, cockpit will not allow items to be created without a valid valid for this field both on the Admin UI and throught he API).
* _Localize_: if the field is localized, the item field value can change from language to language. More about localization in the [Internatiolazation Page](i18n-page).

Below a screenshot of two fields we created and their configuration:

![name field configuration](./create-a-collection-9.png)

![name field configuration](./create-a-collection-7.png)

![role field configuration](./create-a-collection-8.png)

## List collection items

(TODO)

![List Collection Items](./list.png)

## Edit a collection item

(TODO)

![Edit Collection Item](./edit.png)

You will get an easy to use entry form to manage your content items.

## API

### /api/collections/collection/{collectionname}

Get collection schema

```javascript
fetch("/api/collections/collection/posts?token=xxtokenxx")
  .then(collection => collection.json())
  .then(collection => console.log(collection));
```

### /api/collections/get/{collectionname}

Get collection entries

```javascript
fetch("/api/collections/get/posts?token=xxtokenxx")
  .then(res => res.json())
  .then(res => console.log(res));
```

```javascript
fetch('/api/collections/get/posts?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        filter: {published:true},
        limit: 10,
        skip: 5,
        sort: {_created:-1},
        populate: 1 // resolve linked collection items
    }))
    .then(res=>res.json())
    .then(res => console.log(res));
```

### /api/collections/save/{collectionname}

Create / Update collection collection entries

```javascript
fetch('/api/collections/save/posts?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        data: {...}
    }))
    .then(res=>res.json())
    .then(entry => console.log(entry));
```
