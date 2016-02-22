---
title: Visualization
taxonomy:
    category: docs
---

The YDS Library includes a number of visualization components ranging from
map, line and bar charts to pie and grid widgets. In the following paragraphs,
we present thoroughly each component along with the available
customization options.

##### 1. Heat Map Component:

The 'Heat Map' component is based on the Highmaps visualization library. It is a
map component which allows users to depict countries with different colors depending
on the data provided for each country. The developers are able to define the range
of countries or continents shown inside the map as well as the color range which
will be used throughout the map. In case that the map is initialized in continent
level, users are able to click on a country in order to access a more detailed view
of the selected country.

> **Example Usage:**

```html
<div yds-heatmap init-area="Europe"></div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **init-area** (optional) | String attribute, which defines the initialization area of the heat map component. If empty, it initializes a world map instance. Available options: Europe, Greece, Colombia etc.|

> **Screenshot:**

![Heat Map Component](/user/images/heatmap.jpg)

##### 2. Map Component:

The 'Map' component is based on the Leaflet JavaScript library , an open-source library
for mobile-friendly interactive maps. It is a map component which can be used in order
to display a specific route on a map. The displayed route is being retrieved through a
REST API by declaring its unique identifier in the corresponding attribute of the component.
The user is able to zoom to a specific portion of the map as well as to navigate to other
locations. Moreover, the map component allows users to embed it on their own websites using
an iframe element.

> **Example Usage:**

```html
<div yds-map
    project-id="200122"
    embeddable="true"
    embed-btn-x="520"
    embed-btn-y="12"
    popover-pos="left">
</div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **embeddable** (optional) | Boolean attribute, which defines if the map component can be embedded or not.<br>Available options : true, false<br>Default: false |
| **embed-btn-x** (optional) | Numeric attribute, which defines the x-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **embed-btn-y** (optional) | Numeric attribute, which defines the y-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **popover-pos** (optional) | Attribute which defines from which side of the embed button, the embed information window will appear.<br>Available options : right, left, top, bottom<br>Default: right |

> **Screenshot:**

![Search Filters Component](/user/images/map.jpg)

##### 3. Line Chart Component:

The 'Line Chart' component is based on the Highstock visualization library . It consists of a
2D plot of time - series data. The library can zoom into predefined time periods, or into custom
time periods by means of the two date boxes on the top right corner.
The zoom can also be altered graphically, by dragging the bottom right navigation bar left or
right. The plot may be persisted using the two different buttons on the top right corner. On the right
side, there is the ‘extract’ button, which provides the option to extract the plot in various image
formats, or print the plot directly. On the left of this button is the ‘embed’ button, which provides
embedding functionality of the component.

> **Example Usage:**

```html
<div yds-line
    project-id="200122"
    embeddable="true"
    embed-btn-x="520"
    embed-btn-y="12"
    popover-pos="left">
<div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **embeddable** (optional) | Boolean attribute, which defines if the map component can be embedded or not.<br>Available options : true, false<br>Default: false |
| **embed-btn-x** (optional) | Numeric attribute, which defines the x-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **embed-btn-y** (optional) | Numeric attribute, which defines the y-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **popover-pos** (optional) | Attribute which defines from which side of the embed button, the embed information window will appear.<br>Available options : right, left, top, bottom<br>Default: right |

> **Screenshot:**

![Line Chart Component](/user/images/line.jpg)

##### 4. Bar Chart Component:

The 'Bar Chart' component is based on the Highcharts library. It is a highly customizable chart library with the following features:

+ HTML formatted title and subtitle
+ HTML formatted tooltip
+ Customizable padding and width
+ Customizable colors on each bar group
+ Directly printable document via a menu selection
+ Directly exportable document as an image via a menu selection

The library is extended in the context of the YDS platform to support embed functionality, via a menu selection.

> **Example Usage:**

```html
<div yds-bar
    project-id="200122"
    embeddable="true"
    embed-btn-x="520"
    embed-btn-y="12"
    popover-pos="left">
<div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **embeddable** (optional) | Boolean attribute, which defines if the map component can be embedded or not.<br>Available options : true, false<br>Default: false |
| **embed-btn-x** (optional) | Numeric attribute, which defines the x-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **embed-btn-y** (optional) | Numeric attribute, which defines the y-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **popover-pos** (optional) | Attribute which defines from which side of the embed button, the embed information window will appear.<br>Available options : right, left, top, bottom<br>Default: right |

> **Screenshot:**

![Bar Chart Component](/user/images/bar.jpg)

##### 4. Pie Chart Component:

The 'Pie Chart' component is based on the Highcharts JavaScript library, a library for creating pie plots for visualizing data.
A pie chart is a circular chart divided into sectors which is proportional to the quantity it represents. The library comes with a handful of visualization features, such as:

+ Configuration of colors, margins, paddings of the plot
+ Ability to easily render plots from large datasets, with a highly configurable API
+ HTML configurable title and tooltip

The component is extended in the context of the YDS platform to support embed functionality.

> **Example Usage:**

```html
<div yds-pie
    project-id="200122"
    embeddable="true"
    embed-btn-x="520"
    embed-btn-y="12"
    popover-pos="left">
<div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **embeddable** (optional) | Boolean attribute, which defines if the map component can be embedded or not.<br>Available options : true, false<br>Default: false |
| **embed-btn-x** (optional) | Numeric attribute, which defines the x-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **embed-btn-y** (optional) | Numeric attribute, which defines the y-axis position of the embed button.<br>Default: 12 (12px from the top left corner of the component) |
| **popover-pos** (optional) | Attribute which defines from which side of the embed button, the embed information window will appear.<br>Available options : right, left, top, bottom<br>Default: right |

> **Screenshot:**

![Pie Chart Component](/user/images/pie.jpg)

##### 5. Grid Component:

The 'Grid' component is based on the ag-Grid JavaScript library , a powerful library for
creating data grids with large volumes of data. Users are able to navigate with ease through
the displayed data by using its pagination features. They can also sort the displayed data (ascending/descending)
based on a specific column of the table by clicking on the header of the corresponding column. Moreover,
users have the ability to reorder and resize the columns of the grid according to their needs.

> **Example Usage:**

```html
<div yds-grid
    project-id="200110"
    table-type="SubProjectDataGrid"
    sorting="true"
    col-resize="true"
    paging="true"
    page-size="50">
</div>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** (required) | Numeric attribute, which defines the unique identifier of the resource that the displayed route is associated with. If empty, the element cannot be initialized. |
| **data-type** (required) | String attribute that defines the declarative name of the table which contains the data to be rendered. |
| **sorting** (optional) | Boolean attribute, which defines if the columns of the grid will allow content sorting on click.<br>Available options : true, false<br>Default: false |
| **paging** (optional) | Boolean attribute, which defines if the grid display will be paginated or not. If true, the grid rows will be divided in different views.<br>Available options : true, false<br>Default: false |
| **page-size** (optional) | Numeric attribute that defines the rows per page of the paginated grid display.<br>Available options: 0-10000<br>Default: 100 |

> **Screenshot:**

![Grip Component](/user/images/grid.jpg)