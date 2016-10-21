---
title: Sorting
taxonomy:
    category: docs
---

The server supports requests to sort resource collections according to one or more criteria ("sort fields").

>>>>> Although recommended, sort fields do not necessarily need to correspond to resource attribute and association names.

>>>>> It is recommended that dot-separated (U+002E FULL-STOP, ".") sort fields be used to request sorting based upon relationship attributes. For example, a sort field of public-project.title could be used to request that the primary data be sorted based upon the title attribute of the public project relationship.

The endpoint supports requests to sort the primary data with a sort query parameter. The value for sort represents sort fields.

```
GET /aid-activities?sort=title HTTP/1.1
Accept: application/vnd.api+json
```

An endpoint MAY support multiple sort fields by allowing comma-separated (U+002C COMMA, ",") sort fields. Sort fields will be applied in the order specified.

```
GET /aid-activities?sort=title,description HTTP/1.1
Accept: application/vnd.api+json
```

The sort order for each sort field is ascending unless it is prefixed with a minus (U+002D HYPHEN-MINUS, "-"), in which case it will be descending.

```
GET /aid-activities?sort=-title HTTP/1.1
Accept: application/vnd.api+json
```

The above example should return the title of the aid activities sorted in a descending order. 

If the server does not support sorting as specified in the query parameter sort, it will return 400 Bad Request.

If sorting is supported by the server and requested by the client via query parameter sort, the server returns elements of the top-level data array of the response ordered according to the criteria specified. The server will apply default sorting rules to top-level data if request parameter sort is not specified.

>>>>> This section applies to any endpoint that responds with a resource collection as primary data, regardless of the request type.
