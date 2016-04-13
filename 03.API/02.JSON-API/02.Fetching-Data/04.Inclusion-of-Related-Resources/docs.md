---
title: Inclusion of Related Resources
taxonomy:
    category: docs
---

Inclusion of Related Resources

An endpoint MAY return resources related to the primary data by default.

An endpoint MAY also support an include request parameter to allow the client to customize which related resources should be returned.

If an endpoint does not support the include parameter, it MUST respond with 400 Bad Request to any requests that include it.

If an endpoint supports the include parameter and a client supplies it, the server MUST NOT include unrequested resource objects in the included section of the compound document.

The value of the include parameter MUST be a comma-separated (U+002C COMMA, ",") list of relationship paths. A relationship path is a dot-separated (U+002E FULL-STOP, ".") list of relationship names.

If a server is unable to identify a relationship path or does not support inclusion of resources from a path, it MUST respond with 400 Bad Request.

    Note: For example, a relationship path could be comments.author, where comments is a relationship listed under a articles resource object, and author is a relationship listed under a comments resource object.

For instance, comments could be requested with an article:

GET /articles/1?include=comments HTTP/1.1
Accept: application/vnd.api+json

In order to request resources related to other resources, a dot-separated path for each relationship name can be specified:

GET /articles/1?include=comments.author HTTP/1.1
Accept: application/vnd.api+json

    Note: Because compound documents require full linkage (except when relationship linkage is excluded by sparse fieldsets), intermediate resources in a multi-part path must be returned along with the leaf nodes. For example, a response to a request for comments.author should include comments as well as the author of each of those comments.

    Note: A server may choose to expose a deeply nested relationship such as comments.author as a direct relationship with an alias such as comment-authors. This would allow a client to request /articles/1?include=comment-authors instead of /articles/1?include=comments.author. By abstracting the nested relationship with an alias, the server can still provide full linkage in compound documents without including potentially unwanted intermediate resources.

Multiple related resources can be requested in a comma-separated list:

GET /articles/1?include=author,comments.author HTTP/1.1
Accept: application/vnd.api+json

Furthermore, related resources can be requested from a relationship endpoint:

GET /articles/1/relationships/comments?include=comments.author HTTP/1.1
Accept: application/vnd.api+json

In this case, the primary data would be a collection of resource identifier objects that represent linkage to comments for an article, while the full comments and comment authors would be returned as included data.

    Note: This section applies to any endpoint that responds with primary data, regardless of the request type. For instance, a server could support the inclusion of related resources along with a POST request to create a resource or relationship.
