---
title: Search
taxonomy:
    category: docs
process:
	twig: true
---

The Search functionality of the YDS Platform is based on three different
components which are connected with each other. In order for the YDS Search to
operate properly, all the search components must be placed in the same page. 

##### 1. Basic Search Component:

The 'Basic Search' component of the YourDataStories platform is conceived with a
minimal design, towards simplicity and ease of use. The component is composed of
a simple search box and a simple button on the right side of it. The core idea is
the ability to provide results upon any search query (e.g. VAT id, organization name)
provided by the user.

> **Example Usage:**

```html
<yds-search></yds-search>
```

> **Screenshot:**

![Search Bar Component](/user/images/search_bar.jpg)

##### 2. Search Filters Component:

The 'Search Filters' is a component with dynamically generated content based on
the data received from the search query. The generated options can be applied as
filters on the search results in order to provide further exploration functionality
to the end user. In case the user applies a new filter, i.e. select a provided option,
the query mechanism is triggered by the component according to the selected filter
options and a new result set is retrieved.

> **Example Usage:**

```html
<yds-facets></yds-facets>
```

> **Screenshot:**

![Search Filters Component](/user/images/search_filters.jpg)

##### 3. Search Results Component:

The 'Search Results' component consists of a list of result set items. Each
one of these items is composed of the title and a short description of the dataset,
as well as metadata that are retrieved from the search API, depending of the type of
the item. When the user selects an item, the user is redirected in a page that displays
a more detailed view of the dataset, containing general information of the data and the
raw dataset in a customizable grid widget. Moreover, it contains several visualization
components (such as bar charts, pie charts, etc.), which should help the user to draw
useful conclusions around the dataset.

> **Example Usage:**

```html
<yds-results></yds-results>
```

> **Screenshot:**

![Search Results Component](/user/images/search_results.jpg)