---
title: Social
taxonomy:
    category: docs
process:
	twig: true
---

In this page you will find information about how to use the "social" components of the YDS Library, which are components related to social media.

##### 1. Related Items Component:

The Related Items component is used to show a number of related items about a project. These items can be news, blog posts or tweets. There are three tabs for each type of item. By clicking on an item, a new page is opened with the news article, blog post or tweet depending on the item's type. The component also supports loading more items for a category by clicking the "Load more" button that is found on the bottom of each list.

> **Example Usage:**

```html
<yds-related-items
	project-id="http://linkedeconomy.org/resource/Organization/TED_730"
	element-h="300">
</yds-related-items>
```

> **Input Values:**

| Input  | Description |
| ------ | ----------- |
| **project-id** | ID of the project to show items for. |
| **period** | Set the time period of the related items to display. Accepted values: "before", "during" and "after" the project.  |
| **element-h** | Height of the component in pixels. Default is 150 pixels. |
| **total-items** | The component will save the number of total items in this parameter's value (in case you want to display it outside of the component in your page). |

> **Screenshot:**

![Related Items Component](/user/images/related_items.jpg)
