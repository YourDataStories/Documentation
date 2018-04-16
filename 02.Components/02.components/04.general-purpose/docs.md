---
title: General Purpose
taxonomy:
    category: docs
---

The YDS Library includes a few general purpose components
which can be used in order to depict statistics for the YDS Platform as well
as basic information about a specific project.

##### 1. General Statistics Component:

The 'General Statistics' component is an HTML element which depicts general
information about the YDS Platform. When the user visits the page that
contains the specific component, three different animating counters display
selected statistics about the YDS resources.

> **Example Usage:**

```html
<yds-statistics></yds-statistics>
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
<yds-info
    project-id="http://linkedeconomy.org/resource/Subsidy/519339"
    lang="el">
</yds-info>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | String attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **view-type** | String attribute that defines the declarative name of the table which contains the data to be rendered. |
| **lang** | Language of the visualised data |
| **label-col-width** | The number of Bootstrap grid columns the labels should take. Should be between 1-11, default is 4. |
| **vertical** | If true, the info component will have a vertical layout. |
| **base-url** | Base URL to send to the API, so links can be created. Required for some view types (the API will return an error indicating it). |
| **extra-params** | Object with extra parameters to send in the request to the API. |

> **Screenshot:**

![Project Info Component](/user/images/project_info.jpg)

##### 3. Aggregate Component:

This component is used to show a single aggregated value for some aspect of the data in the YDS Platform. For example the number of sectors, budget amount or even a date can be shown. The component can have multiple layouts which are defined by the API for each view type, but most of the time there is a title and a value. It can also take as input an object with more parameters, such as a year range or a list of specific countries in order to filter the displayed value. The accepted parameters for this object vary with the Aggregate's view type and depend on the JSON-LD API.

> **Example Usage:**

```html
<yds-aggregate
    project-id="http://linkedeconomy.org/resource/Contract/AwardNotice/6723325"
    view-type="contract.tenders.number"
    element-h="150"
    icon-size="3">
</yds-aggregate>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** | String attribute, which defines the unique identifier of the resource that the displayed aggregated value is associated with. Default value is "none" |
| **view-type** (required) | String attribute that defines the declarative name of the table which contains the data to be rendered. |
| **lang** | Language of the visualised data. |
| **base-url** | Base URL to send to the API, so links can be created in the component contents. Required for some view types (the API will return an error indicating it). |
| **extra-params** | Object with extra parameters to send in the request to the API. |
| **icon-size** | Number between 2-5, sets the size of the Aggregate's icon, in the view types that show icons. Default size is 4. |
| **show-view-btn** | Set to true to display a "View details" button in the bottom of the aggregate. Not available for all layouts.  |
| **element-h** | Minimum height of the component in pixels. Default is 140 pixels. |
| **max-height** | Maximum height of the component in pixels. Works only for the "title" layout, and will scroll if the specified height is exceeded. |

> **Screenshot:**

![Aggregate Component](/user/images/aggregate.jpg)
