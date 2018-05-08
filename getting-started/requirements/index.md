uid: pid-57cc6673eeb35
type: documentation/page
created: 2016-09-04 18:22:43
modified: 2016-09-05 23:47:09
title: Requirements
sort: 1

===

- PHP >= 7.1
- PHP extensions enabled: iconv gd pdo zip opcache pdo_sqlite
- SQLite or MongoDB (needs mongodb from PECL besides)
- Apache (with mod_rewrite and mod_expires) or nginx
- Any modern Browser

---

**That's it.** No generation or build scripts, no heavy-weight PHP libraries or dependencies.
Cockpit was successfully tested on Apache and nginx.
