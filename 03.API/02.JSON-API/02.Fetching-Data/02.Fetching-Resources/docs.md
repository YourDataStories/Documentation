---
title: Fetching Resources
taxonomy:
    category: docs
---

The server supports fetching resource data for every URL provided as:

+ a self link as part of the top-level links object
+ a self link as part of a resource-level links object
+ a related link as part of a relationship-level links object

For example, the following request fetches a collection of trade activities:

```
GET /api/mudcat/trade-activities HTTP/1.1
Host: platform.yourdatastories.eu
```

The following request fetches a trade activity:

```
GET /api/mudcat/trade-activities/4b8f1a8889220d228a0a9e39a3bbd6e3 HTTP/1.1
Host: platform.yourdatastories.eu
```

And the following request fetches the origin of a trade activity:

```
GET /api/mudcat/trade-activities/4b8f1a8889220d228a0a9e39a3bbd6e3/origin HTTP/1.1
Host: platform.yourdatastories.eu
```

Responses

```
200 OK
```

The server responds to a successful request to fetch an individual resource or resource collection with a 200 OK response.

The server responds to a successful request to fetch a resource collection with an array of resource objects or an empty array ([]) as the response document's primary data.

For example, a GET request to a collection of trade activities could return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json
 {
            "attributes": {
                "financial-year": "2011-01-01Z"
            },
            "id": "800466d9a46544d1759be3cdad6d5fa2",
            "type": "trade-activities",
            "relationships": {
                "concerns": {
                    "links": {
                        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/concerns",
                        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/concerns"
                    }
                },
                "origin": {
                    "links": {
                        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/origin",
                        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/origin"
                    }
                },
                "destination": {
                    "links": {
                        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/destination",
                        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/destination"
                    }
                },
                "amount": {
                    "links": {
                        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/amount",
                        "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/amount"
                    }
                }
            }
        }
```

A similar response representing an empty collection would be:
```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/trade-activities/"
  },
  "data": []
} 
```
The server responds to a successful request to fetch an individual resource with a resource object or null provided as the response document's primary data.

null is only an appropriate response when the requested URL is one that might correspond to a single resource, but doesn't currently.

>>>>> Consider, for example, a request to fetch a to-one related resource link. This request would respond with null when the relationship is empty (such that the link is corresponding to no resources) but with the single related resource's resource object otherwise.

For example, a GET request to an individual trade activity could return:
```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  {
    "data": {
        "attributes": {
            "financial-year": "2011-01-01Z"
        },
        "id": "800466d9a46544d1759be3cdad6d5fa2",
        "type": "trade-activities",
        "relationships": {
            "concerns": {
                "links": {
                    "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/concerns",
                    "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/concerns"
                }
            },
            "origin": {
                "links": {
                    "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/origin",
                    "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/origin"
                }
            },
            "destination": {
                "links": {
                    "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/destination",
                    "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/destination"
                }
            },
            "amount": {
                "links": {
                    "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/links/amount",
                    "related": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/amount"
                }
            }
        }
    },
    "links": {
        "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2"
    }
}
```

If the above trade activity's destination is missing, then a GET request to that related resource would return:

```
HTTP/1.1 200 OK
Content-Type: application/vnd.api+json

{
  "links": {
    "self": "/trade-activities/800466d9a46544d1759be3cdad6d5fa2/destination"
  },
  "data": null
}
```

```
404 Not Found
```

The server responds with 404 Not Found when processing a request to fetch a single resource that does not exist, except when the request warrants a 200 OK response with null as the primary data (as described above).

Other Responses

+ The server MAY respond with other HTTP status codes.

+ The server MAY include error details with error responses.

+ The server prepares responses, and the client interprets responses, in accordance with HTTP semantics.
