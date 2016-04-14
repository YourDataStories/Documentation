---
title: 'Building a Drupal Module using a YDS Component'
---

This tutorial describes the steps to include a YDS component in a Drupal 7 custom module.
A working example can be seen at [platform.yourdatastories.eu/geo-editing](http://platform.yourdatastories.eu/geo-editing)

###Summary
- Prerequites
- Setup
- Custom Block
- Block Template
- Component angular file

### Prerequites
This tutorial assumes basic knowledge of creating a custom drupal module. You can follow this [tutorial](https://www.drupal.org/node/1074360) for a detailed description of how to setup and deploy a custom module in Drupal 7.
For the purposes of this tutorial, the YDS [Geo-Editing Component](http://ydsdev.iit.demokritos.gr/YDS-docs/Components/components/Geo-Editing) will be used. As described in it's documentation, the component is developed using [angular.js](https://angularjs.org/). Even though knowing how to build an application with angular is not obligatory in order to create the Drupal module, it would be helpful to understand some of the concepts below.




###Setup
Let's call our module **yds_geo_editing** The standard module files have to be initially created:

 1. yds_geo_editing.info
 
        name = yds_project
        description = Use of the YDS Geo Editing Component
        core = 7.x

 2. yds_geo_editing.module
 
Moreover, the component's js and css files should be put in the module's folder structure as seen in the screenshot below

![Module folder structure](http://platform.yourdatastories.eu/sites/default/files/ydsdrupalfolderstructure.PNG)

Finally, the following statement includes the declaration of the angular application

	<body data-ng-app="yds">

The **data-ng-app="yds"** attribute should be put at the body tag of the page where the module will reside. This can be found usually in the html.tpl.php file of the theme that is used in our Drupal website.

###Custom Block

 The contents of the yds_geo_editing.module file should be the following:
 
```php
<?php
function yds_project_block_info() {
	$blocks['yds_geo_editing'] = array(
		'info' => t('YDS Geo Editing'),
	        );
	return $blocks;
}

function yds_geo_editing_block_view($delta = '') {
	$block = array();      
	drupal_add_js(array( 'yds_geo_editing' => array('modulePath' => drupal_get_path('module','yds_geo_editing'))),'setting');
     
	switch ($delta) {
          case 'yds_geo_editing':
	          $path = drupal_get_path('module', 'yds_geo_editing');
	          $block['subject'] = t('Geo Editing');
	          $block['content'] = array(
		  	'#theme' => 'geo_editing',
		        '#attached' => array(
		               'css' => array(
		    		   $path . '/css/bootstrap2.min.css',
		    		   $path . '/css/custom-ncsr.css',
		    		   $path . '/css/theme-fresh.min.css',
		    		   $path . '/css/leaflet.contextmenu.css',
		    		   $path . '/css/leaflet.css',
		    		   ),
			    	'js' => array(
		          	$path . '/js/merged-lib-min.js',
		          	$path . '/js/yds-lib.js',
    			        $path . '/js/components/geo-editing.js',    
		                ),		  
		        ),
		  );
          break; 	  
	}
	return $block;
}
	    
function yds_project_theme() {
  	return array(
		'geo_editing' => array(
      		'template' => 'geo-editing',
      		'variables' => array(),
    		),	
  	);
}
```

The yds_geo_editing_block_view function includes the statements that load the required css and js files in order to display the map editing component. Moreover, the following statement:

	drupal_add_js(array( 'yds_geo_editing' => array('modulePath' => drupal_get_path('module','yds_geo_editing'))),'setting');

is responsible to add our module's path to the settings array of Drupal. This is necessary for the definition of the angular template later.

###Block template

 The contents of the geo-editing.tpl.php file should be the following:
 
 ```php
 <?php
/**
 * @file
* AngularJS template to render a project's details
*/
?>
    
<yds-geo-editing project-id="1" ></yds-geo-editing>    
 
 ```
This file actually includes only the declaration of the angular tag that is going to render the geo-editing component.
The component's angular template file which is included in the templates folder (templates/geo-editing.html) is going to do all the rest of the angular templating process.

###Component angular file
The js folder includes the yds-lib.js file which is responsible for the initialisation of the angular application. The geo-editing.js file includes the angular directive for the geo-editing component. The later had to be adapted in order to fix the path to the component's template file. Specifically:

```javascript
angular.module('yds').directive('ydsGeoEditing', ['Data', '$timeout', function(Data, $timeout){
	return {
       		restrict: 'E',
       		scope: {
       			projectId: '@'
        		},
       	templateUrl:Drupal.settings.basePath + Drupal.settings.yds_project.modulePath + '/templates/geo-editing.html',
       	link: function(scope, elem, attrs) {
       	... /*rest remain the same*/
```

The templateUrl above uses Drupal's variable for basepath together with the variable that we defined in the .module file of our module. This provides the correct path to our module's templates folder.
