---
layout: post
title: "Couch Db: Ready For Primetime?"
date: 2009-05-26 16:04
comments: true
tags: [couchdb databases meeting]
---
[Colin Alstad] gave a very nice presentation on [CouchDB] today at the [Upstate.rb User Group][urb]. Being a new technology and such a vast departure from the industry standard ([RDBMS]), it has a lot of proving to do. It doesn't claim to be a replacement for the relational model, but for a developer, or a company for that matter, to leave SQL behind and use a document oriented database will take some convincing.

On a positive note, I really do like the concept. HTTP Server, restful architecture, schema-less design. The built in replication and versioning is amazing. In practice however, I still need more control. Most, really all, the apps I build are for businesses. The have lots of requirements when it comes to data. The end up as contraints in the database. This is simply not possible to do with CouchDB.

For instance, I created a User object (backed by [CouchRest]) in a small [Sinatra] app I was playing building. As I was working on the authentication, I needed a unique email address across all users. [CouchDB] documents only have one unique id to distinguish them in the database. You can specify this or you can allow [CouchDB] to create it for you. That is the only unique value that is enforced. So if you also want a field, such as an email address, that is unique you are out of luck. I imagine that you'd have to have a view that checks all the User documents for that email prior to creating a record.

I'm really interested to see what the sweet spot of [CouchDB] will become. It has a lot of promise, but as of now, I'm not convinced **yet**.

![CouchDB Logo]

[Colin Alstad]: http://twitter.com/calstad
[urb]: http://upstaterb.org
[CouchDB]: http://couchdb.apache.org/
[CouchDB Logo]: http://couchdb.apache.org/img/couchdb-logo.png
[RDBMS]: http://en.wikipedia.org/wiki/RDBMS
[CouchRest]: http://github.com/jchris/couchrest/tree/master
[Sinatra]: http://www.sinatrarb.com/