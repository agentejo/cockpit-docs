uid: pid-57cd7ge46c809
type: documentation/page
created: 2016-09-05 14:15:00
modified: 2016-09-05 14:15:00
title: Cockpit
sort: 1

===


### /api/cockpit/authUser

Authenticate user

```javascript
fetch('/api/cockpit/authUser?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        user: 'username',
        password: 'xxpasswordxx'
    })
})
.then(user => res.json())
.then(user => console.log(user));
```

### /api/cockpit/saveUser

Create / Update user

```javascript
fetch('/api/cockpit/saveUser?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        user: {...} // user data (user, name, email, active, group)
    })
})
.then(user => res.json())
.then(user => console.log(user));
```

### /api/cockpit/listUsers

Get users.

```javascript
fetch('/api/cockpit/listUsers?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        filter: {...}
    })
})
.then(users => users.json())
.then(users => console.log(users));
```

### /api/cockpit/assets

Get assets

```javascript
fetch('/api/cockpit/assets?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        filter: {...}
    })
})
.then(assets => assets.json())
.then(assets => console.log(assets));
```

### /api/cockpit/image

Get thumbnail url

```javascript
fetch('/api/cockpit/image?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        src: imagePath || asset._id,
        m: ('thumbnail' | 'bestFit' | 'resize' | 'fitToWidth' | 'fitToHeight'),
        w: (int),
        h: (int),
        q: (int),
        b64: (boolean)
    })
})
.then(url => url.text())
.then(url => console.log(url));
```

```html
<img src="/api/cockpit/image?token=xxtokenxx&src=path&width=200&height=200&output=true">
```