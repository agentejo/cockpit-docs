uid: pid-57fd7de46c8s9
type: documentation/page
created: 2018-08-17 14:15:00
modified: 2018-08-17 14:15:00
title: Singletons
sort: 3

===

### /api/singletons/listSingletons

Get all singletons

```javascript
fetch('/api/singletons/listSingletons?token=xxtokenxx')
    .then(singletons => singletons.json())
    .then(singletons => console.log(singletons));
```

### /api/singletons/get/{singletonname}

Get singleton data.

```javascript
fetch('/api/singletons/get/{singletonname}?token=xxtokenxx')
    .then(data => data.json())
    .then(data => console.log(data));
```
