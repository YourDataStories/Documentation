---
title: Sorting
taxonomy:
    category: docs
---

A server MAY choose to support requests to sort resource collections according to one or more criteria ("sort fields").

>>>>> Although recommended, sort fields do not necessarily need to correspond to resource attribute and association names.

>>>>> It is recommended that dot-separated (U+002E FULL-STOP, ".") sort fields be used to request sorting based upon relationship attributes. For example, a sort field of author.name could be used to request that the primary data be sorted based upon the name attribute of the author relationship.

An endpoint MAY support requests to sort the primary data with a sort query parameter. The value for sort MUST represent sort fields.

```
GET /people?sort=age HTTP/1.1
Accept: application/vnd.api+json
```

An endpoint MAY support multiple sort fields by allowing comma-separated (U+002C COMMA, ",") sort fields. Sort fields SHOULD be applied in the order specified.

```
GET /people?sort=age,name HTTP/1.1
Accept: application/vnd.api+json
```

The sort order for each sort field MUST be ascending unless it is prefixed with a minus (U+002D HYPHEN-MINUS, "-"), in which case it MUST be descending.

```
GET /articles?sort=-created,title HTTP/1.1
Accept: application/vnd.api+json
```

The above example should return the newest articles first. Any articles created on the same date will then be sorted by their title in ascending alphabetical order.

If the server does not support sorting as specified in the query parameter sort, it MUST return 400 Bad Request.

If sorting is supported by the server and requested by the client via query parameter sort, the server MUST return elements of the top-level data array of the response ordered according to the criteria specified. The server MAY apply default sorting rules to top-level data if request parameter sort is not specified.

>>>>> This section applies to any endpoint that responds with a resource collection as primary data, regardless of the request type.
