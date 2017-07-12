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
provided by the user. It also supports displaying search suggestions to the user
as they type in the text field, with a customizable amount of suggestions.

> **Example Usage:**

```html
<yds-search></yds-search>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **lang** | Language of the component's interface |
| **max-suggestions** | Maximum amount of suggestions to show in the suggestions dropdown (Default: 15) |
| **standalone** | Boolean attribute, set to true if you want the search results to be shown in a new page instead of directly under the search bar. (Default: false) |
| **tabbed** | Boolean attribute, set to true when the Basic Search component is used in the Tabbed Search (explained in more detail on the next page). It enables Advanced Search, however you must also set the **concept** and **concept-id** attributes. Setting **standalone** and **tabbed** to true at the same time is not supported. |
| **concept-id** | String attribute, needed only for Tabbed Search. Defines the ID of the concept that the Advanced Search should use to get the available filters from the API. |
| **concept** | String attribute, needed only for Tabbed Search. Defines the name of the concept that the Advanced Search will get rules for. |

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

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **lang** | Language of the displayed filter labels |

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

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **lang** | Language of the displayed results |
| **user-id** | Set the logged in user's ID to enable saving results to the Library |

> **Screenshot:**

![Search Results Component](/user/images/search_results.jpg)