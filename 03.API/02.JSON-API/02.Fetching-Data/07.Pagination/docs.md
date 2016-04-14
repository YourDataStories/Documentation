---
title: Pagination
taxonomy:
    category: docs
---

The server can limit the number of resources returned in a response to a subset ("page") of the whole set available.

The server can provide links to traverse a paginated data set ("pagination links").

Pagination links appear in the links object that corresponds to a collection. To paginate the primary data, supply pagination links in the top-level links object. To paginate an included collection returned in a compound document, supply pagination links in the corresponding links object.

The following keys are used for pagination links:

+ first: the first page of data
+ last: the last page of data
+ prev: the previous page of data
+ next: the next page of data

Keys will either be omitted or have a null value to indicate that a particular link is unavailable.

Concepts of order, as expressed in the naming of pagination links, remain consistent with JSON API's sorting rules.

The page query parameter is reserved for pagination. Servers and clients use this key for pagination operations.

>>>>> JSON API is agnostic about the pagination strategy used by a server. Effective pagination strategies include (but are not limited to): page-based, offset-based, and cursor-based. The page query parameter can be used as a basis for any of these strategies. For example, a page-based strategy might use query parameters such as page[number] and page[size], an offset-based strategy might use page[offset] and page[limit], while a cursor-based strategy might use page[cursor].

>>>>> The example query parameters above use unencoded [ and ] characters simply for readability. In practice, these characters must be percent-encoded, per the requirements in RFC 3986.

>>>>> This section applies to any endpoint that responds with a resource collection as primary data, regardless of the request type.
