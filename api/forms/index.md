uid: pid-51fd7de46c8s9
type: documentation/page
created: 2018-08-18 20:15:00
modified: 2018-08-18 20:15:00
title: Forms
sort: 4

===

### /api/forms/submit/{form_name}

Stores the submission of a form as an entry.

```javascript
fetch('/api/forms/submit/cockpitForm?token=xxtokenxx', {
    method: 'post',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
        form: {
            field1: 'value1',
            field2: 'value2'
        }
    })
})
.then(entry => entry.json())
.then(entry => console.log(entry));
```
