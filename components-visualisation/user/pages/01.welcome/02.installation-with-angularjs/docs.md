---
title: Installation
taxonomy:
    category: docs
---

The YDS Visualisation library depends on a number of trird party libraries such as AngularJS, Hicharts etc. Below you will find a complete list with its dependencies.


##### List of required dependencies:

+ AngularJS (v1.4.7)
+ Bootstrap (v0.14.3)
+ ag-Grid (v2.3.5)
+ Highstock (v2.1.9)
+ Highmaps (v1.1.9)
+ LeafletJS (v0.7.7)
+ UnderscoreJS (v1.8.3)
+ oclazyload (v1.0.8)

>>>> For an unobstructive installation process, avoid to include lower versions of the aforementioned libraries.

##### Installation Process:
**Step 1: **Import the required dependencies inside your's website head section:

```html
<!-- Bootstrap core CSS -->
<link href="css/bootstrap.min.css" rel="stylesheet">
<link href="css/custom.css" rel="stylesheet">

<link href="css/ag-grid.min.css" rel="stylesheet">
<link href="css/theme-fresh.min.css" rel="stylesheet">
<link href="css/leaflet.css" rel="stylesheet">
<link href="css/leaflet.contextmenu.css" rel="stylesheet">

<!-- Import leaflet library -->
<script src="lib/leaflet.js"></script>
<script src="lib/leaflet.contextmenu.js"></script>

<!-- Import ag-grid library -->
<script src="lib/ag-grid.min.js"></script>

<!-- Import highstock(includes highcharts) along with the highmap module -->
<script src="lib/highcharts-standalone.src.js"></script>
<script src="lib/highstock.js"></script>
<script src="lib/highmaps.min.js"></script>
<script src="lib/highstock-exporting.js"></script>

<script src="lib/underscore-min.js"></script>
<script src="lib/angular.min.js"></script>
<script src="lib/angular-ui-router.min.js"></script>
<script src="lib/angular.ng-modules.js"></script>

<script src="lib/ocLazyLoad.min.js"></script>
<script src="lib/ui-bootstrap-tpls-0.14.3.min.js"></script>
```
**Step 2: **Import the file which includes YDS Library:
```html
<script src="js/yds-lib.js"></script>
```

**Step 3: **Inject the YDS module inside you AngularJS application (app.js):
```js
var ydsDemo = angular.module('ydsDemo', ['yds']);
```

>>>>> In case you have completed successfully the installation process, you are ready to
explore and leverage the capabilities of the YDS library. In case you want to try it out first,
visit the [YDS Demo Website](http://ydsdev.iit.demokritos.gr/YDSComponents/#/ "Visit YDS Demo Website!").