---
title: Geo-Editing
taxonomy:
    category: docs
---

The component consists of an interactive map, upon which the user may provide road traces.
On the right side, a map is displayed. The user can zoom in/out, and add starting, ending,
and via points to the map, defining a route to be stored. The component will automatically
generate the route, based on the roads found from the underlying map. On the left of the map,
the route points provided by the user are displayed, where the user can delete any of them
according to his desires. Below the map, two buttons reside, a “Clear All” button, providing
a ‘remove all adjustments’ functionality to the component, and a “Save” button, providing
persistence of the route generated. The component may be used, for example, when a project
involves road construction works, a user may provide the actual road that is being developed,
if the data is not already present in the platform. In order to achieve this desired functionality,
the service calls an underlying API (GeoEditing) that extracts geolocation data from the
open source OpenRouteService  and prints them properly to the map.

> **Example Usage:**

```html
<yds-geo-editing project-id="1" ></yds-geo-editing>
```

> **Screenshot:**

![Search Filters Component](/user/images/geo_editing.jpg)