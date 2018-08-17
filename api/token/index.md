uid: pid-57cd7de46c809
type: documentation/page
created: 2016-09-05 14:15:00
modified: 2016-09-05 14:15:00
title: API Token
sort: 0

===

Before accessing your data you need to create an API token. To do so please go to _Settings > API Access_ to generate yown unique API token. You can re-generate the token anytime you want.

![Create Token](webtoken.png)

### Custom API Tokens

*Custom keys* can be added as required. Each key has a set of Rules which specify which API endpoints the token is valid for. The default rule `*` means all endpoints.

To limit the token you can specify one permitted endpoint per line.

For example, let's say you just want to allow the collections get api, then the Rules should contain

`/api/collections/get`

If you just want to allow to query the posts collection with the token, then the Rules for this are:

`/api/collections/get/posts`

Or `/api/collections/get/(authors|posts)` for multiple collections.