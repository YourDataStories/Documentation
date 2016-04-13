---
title: Fetching Relationships
taxonomy:
    category: docs
---

A server MUST support fetching relationship data for every relationship URL provided as a self link as part of a relationship's links object.

For example, the following request fetches data about an article's comments:

```
GET /articles/1/relationships/comments HTTP/1.1
Accept: application/vnd.api+json
```

And the following request fetches data about an article's author:

```
GET /articles/1/relationships/author HTTP/1.1
Accept: application/vnd.api+json
```

Responses
200 OK

A server MUST respond to a successful request to fetch a relationship with a 200 OK response.

The primary data in the response document MUST match the appropriate value for resource linkage, as described above for relationship objects.

The top-level links object MAY contain self and related links, as described above for relationship objects.

For example, a GET request to a URL from a to-one relationship link could return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/articles/1/relationships/author",
    "related": "/articles/1/author"
  },
  "data": {
    "type": "people",
    "id": "12"
  }
}
```

If the above relationship is empty, then a GET request to the same URL would return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/articles/1/relationships/author",
    "related": "/articles/1/author"
  },
  "data": null
}
```

A GET request to a URL from a to-many relationship link could return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/articles/1/relationships/tags",
    "related": "/articles/1/tags"
  },
  "data": [
    { "type": "tags", "id": "2" },
    { "type": "tags", "id": "3" }
  ]
}
```

If the above relationship is empty, then a GET request to the same URL would return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/articles/1/relationships/tags",
    "related": "/articles/1/tags"
  },
  "data": []
}
```

404 Not Found

A server MUST return 404 Not Found when processing a request to fetch a relationship link URL that does not exist.

>>>>> This can happen when the parent resource of the relationship does not exist. For example, when /articles/1 does not exist, request to /articles/1/relationships/tags returns 404 Not Found.

If a relationship link URL exists but the relationship is empty, then 200 OK MUST be returned, as described above.
Other Responses

+ A server MAY respond with other HTTP status codes.

+ A server MAY include error details with error responses.

+ A server MUST prepare responses, and a client MUST interpret responses, in accordance with HTTP semantics.