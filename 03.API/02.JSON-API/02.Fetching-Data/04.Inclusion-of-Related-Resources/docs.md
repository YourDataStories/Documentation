---
title: Inclusion of Related Resources
taxonomy:
    category: docs
---

An endpoint MAY return resources related to the primary data by default.

An endpoint MAY also support an include request parameter to allow the client to customize which related resources should be returned.

If an endpoint supports the include parameter and a client supplies it, the server does not include unrequested resource objects in the included section of the compound document.

The value of the include parameter is a comma-separated (U+002C COMMA, ",") list of relationship paths. A relationship path is a dot-separated (U+002E FULL-STOP, ".") list of relationship names.

If the server is unable to identify a relationship path or does not support inclusion of resources from a path, it responds with 400 Bad Request.

>>>>> For example, a relationship path could be destination.country, where destination is a relationship listed under a trade activity resource object, and country is a relationship listed under a destination resource object.

For instance, concerns could be requested with a trade activity:

```
GET trade-activities/800466d9a46544d1759be3cdad6d5fa2?include=destination HTTP/1.1
Accept: application/vnd.api+json
```

In order to request resources related to other resources, a dot-separated path for each relationship name can be specified:

```
GET trade-activities/800466d9a46544d1759be3cdad6d5fa2?include=destination.country HTTP/1.1
Accept: application/vnd.api+json
``` 

>>>>> Because compound documents require full linkage (except when relationship linkage is excluded by sparse fieldsets), intermediate resources in a multi-part path must be returned along with the leaf nodes. For example, a response to a request for destination.country should include a destination as well as the country linked to it.

>>>>> The server may choose to expose a deeply nested relationship such as destination.country as a direct relationship with an alias such as destination-country. This would allow a client to request trade-activities/800466d9a46544d1759be3cdad6d5fa2?include=destination-country instead of trade-activities/800466d9a46544d1759be3cdad6d5fa2?include=destination.country. By abstracting the nested relationship with an alias, the server can still provide full linkage in compound documents without including potentially unwanted intermediate resources.

Multiple related resources can be requested in a comma-separated list:

 ```
GET /trade-activities/800466d9a46544d1759be3cdad6d5fa2?include=concerns,destination.country HTTP/1.1
Accept: application/vnd.api+json
```

>>>>> This section applies to any endpoint that responds with primary data, regardless of the request type. 
