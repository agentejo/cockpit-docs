uid: pid-57fd7de46c8s9
type: documentation/page
created: 2016-09-05 14:15:00
modified: 2016-09-05 14:15:00
title: Regions
sort: 3

===

### /api/regions/listRegions

Get all regions

```javascript
fetch('/api/regions/listRegions?token=xxtokenxx')
    .then(regions => regions.json())
    .then(regions => console.log(regions));
```

### /api/regions/get/{regionname}

Get rendered region template.

```javascript
fetch('/api/regions/get/{regionname}?token=xxtokenxx')
    .then(region => data.text())
    .then(region => console.log(region));
```

### /api/regions/data/{regionname}

Get form data as json.

```javascript
fetch('/api/regions/data/{regionname}?token=xxtokenxx')
    .then(data => data.json())
    .then(data => console.log(data));
```