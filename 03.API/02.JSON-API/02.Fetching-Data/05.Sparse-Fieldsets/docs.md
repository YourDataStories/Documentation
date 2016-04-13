---
title: Sparse Fieldsets
taxonomy:
    category: docs
---

Sparse Fieldsets

A client MAY request that an endpoint return only specific fields in the response on a per-type basis by including a fields[TYPE] parameter.

The value of the fields parameter MUST be a comma-separated (U+002C COMMA, ",") list that refers to the name(s) of the fields to be returned.

If a client requests a restricted set of fields for a given resource type, an endpoint MUST NOT include additional fields in resource objects of that type in its response.

GET /articles?include=author&fields[articles]=title,body&fields[people]=name HTTP/1.1
Accept: application/vnd.api+json

    Note: The above example URI shows unencoded [ and ] characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in RFC 3986.

    Note: This section applies to any endpoint that responds with resources as primary or included data, regardless of the request type. For instance, a server could support sparse fieldsets along with a POST request to create a resource.
