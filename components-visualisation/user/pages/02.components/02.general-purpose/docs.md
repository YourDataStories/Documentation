---
title: General Purpose
taxonomy:
    category: docs
---

The YDS Library includes 2 general purpose components
which can be used in order to depict statistics for the YDS Platform as well
as basic information about a specific project.

##### 1. General Statistics Component:

The 'General Statistics' component is an HTML element which depicts general
information about the YDS Platform. When the user visits the page that
contains the specific component, three different animating counters display
selected statistics about the YDS resources.

> **Example Usage:**

```html
<div yds-statistics></div>
```

> **Screenshot:**

![General Statistics Component](/user/images/general_statistics.jpg)

##### 2. Project Info Component:

The 'Project Info' component is an HTML element which is used to display
information about specific projects or organizations, information about
which is available through the YDS Platform. The amount of the shown
information depends on the type of the resource that the user has visited.

> **Example Usage:**

```html
<div yds-info
    project-id="200122"
    data-type="projectInfo">
</div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **data-type** (required) | String attribute that defines the declarative name of the table which contains the data to be rendered. |

> **Screenshot:**

![Search Filters Component](/user/images/project_info.jpg)
