---
title: Sparse Fieldsets
taxonomy:
    category: docs
---

The client MAY request that an endpoint return only specific fields in the response on a per-type basis by including a fields[TYPE] parameter.

The value of the fields parameter is a comma-separated (U+002C COMMA, ",") list that refers to the name(s) of the fields to be returned.

If the client requests a restricted set of fields for a given resource type, an endpoint does not include additional fields in resource objects of that type in its response.

```
GET /public-projects?fields[public-projects]=project-id HTTP/1.1
Accept: application/vnd.api+json
```

>>>>> The above example URI shows unencoded [ and ] characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in RFC 3986.

>>>>> This section applies to any endpoint that responds with resources as primary or included data, regardless of the request type. For instance, a server could support sparse fieldsets along with a POST request to create a resource.
