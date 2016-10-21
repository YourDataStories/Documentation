---
title: Fetching Relationships
taxonomy:
    category: docs
---

The server supports fetching relationship data for every relationship URL provided as a self link as part of a relationship's links object.

For example, the following request fetches data about a trade activity's concerns:

```
GET /trade-activities/4b8f1a8889220d228a0a9e39a3bbd6e3/concerns HTTP/1.1
Accept: application/vnd.api+json
```

And the following request fetches data about a trade activity's destination:

```
GET /trade-activities/4b8f1a8889220d228a0a9e39a3bbd6e3/destination HTTP/1.1
Accept: application/vnd.api+json
```

```
Responses
200 OK
```

The server responds to a successful request to fetch a relationship with a 200 OK response.

The primary data in the response document matches the appropriate value for resource linkage, as described above for relationship objects.

The top-level links object contains self and related links, as described above for relationship objects.

For example, a GET request to a URL from a to-one relationship link could return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
    "data": {
        "attributes": {},
        "id": "899b59d5360933b672f2f9c07fd3ebf8",
        "type": "group-national-agents",
        "relationships": {
            "country": {
                "links": {
                    "self": "/group-national-agents/899b59d5360933b672f2f9c07fd3ebf8/links/country",
                    "related": "/group-national-agents/899b59d5360933b672f2f9c07fd3ebf8/country"
                }
            }
        }
    },
    "links": {
        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/destination",
        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/destination"
    }
}
```

If the above relationship is empty, then a GET request to the same URL would return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
    "data": null,
    "links": {
        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/destination",
        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/destination"
    }
}
```

A GET request to a URL from a to-many relationship link could return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
    "data": {
        "attributes": {
            "notation": "491110",
            "label": "Printed Matter; Trade Advertising Material, Commercial Catalogues And The Like"
        },
        "id": "12cdb2deec6dee7b1442dec2f49110ae",
        "type": "concepts",
        "relationships": {
            "broader-concepts": {
                "links": {
                    "self": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/links/broader-concepts",
                    "related": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/broader-concepts"
                }
            },
            "narrower-concepts": {
                "links": {
                    "self": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/links/narrower-concepts",
                    "related": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/narrower-concepts"
                }
            },
            "concept-scheme": {
                "links": {
                    "self": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/links/concept-scheme",
                    "related": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/concept-scheme"
                }
            },
            "top-concept-of": {
                "links": {
                    "self": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/links/top-concept-of",
                    "related": "/concepts/12cdb2deec6dee7b1442dec2f49110ae/top-concept-of"
                }
            }
        }
    },
    "links": {
        "self": "/trade-activities/cee39b1afd34f2ec536304461134c0a0/links/concerns",
        "related": "/trade-activities/cee39b1afd34f2ec536304461134c0a0/concerns"
    }
}
```

If the above relationship is empty, then a GET request to the same URL would return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
    "data": [],
    "links": {
        "self": "/trade-activities/cee39b1afd34f2ec536304461134c0a0/links/concerns",
        "related": "/trade-activities/cee39b1afd34f2ec536304461134c0a0/concerns"
    }
}
```

```
404 Not Found
```

The server returns 404 Not Found when processing a request to fetch a relationship link URL that does not exist.

>>>>> This can happen when the parent resource of the relationship does not exist. For example, when /trade-activities/cee39b1afd34f2ec536304461134c0a0/ does not exist, request to /trade-activities/cee39b1afd34f2ec536304461134c0a0/links/concerns returns 404 Not Found.

If a relationship link URL exists but the relationship is empty, then 200 OK MUST be returned, as described above.
Other Responses

+ The server MAY respond with other HTTP status codes.

+ The server MAY include error details with error responses.

test
+ The server prepares responses, and a client interprets responses, in accordance with HTTP semantics.