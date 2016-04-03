---
title: 'JSON-LD API'
---

This section provides some examples regarding the [JSON-LD](http://json-ld.org/) API.

### API for Search
The JSON-LD API provides also access to search (implemented through an [Apache Solr](http://lucene.apache.org/solr/) server), altough the results are **not** in JSON-LD (as results are provided directly from the Solr server in JSON format).

| Action (Search) | API Call |
|-----------------|----------|
| Search with **"Ηρακλειο"** (a misspelled version of the Greek city "Ηράκλειο") | component/search.tcl, q=Ηρακλειο<br><http://platform.yourdatastories.eu/api/json-ld/component/search.tcl?q=Ηρακλειο> |
| Search with "Ηρακλειο" with facet **"Subsidy" | component/search.tcl, q=Ηρακλειο, fq=type:Subsidy<br><http://platform.yourdatastories.eu/api/json-ld/component/search.tcl?q=Ηρακλειο&fq=type:Subsidy> |

### API for Component: **grid**
| Action (Grid Component) | API Call |
|-------------------------|----------|
| Get project with id (**Greek**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=el**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http%3A%2F%2Flinkedeconomy.org%2Fresource%2FSubsidy%2F519339&type=project&lang=el> |
| Get project with id (**English**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=en**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project&lang=en> |
| Get project with id (**all available languages**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=i18n**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project&lang=i18n> |
| Get **types** (facets) supported by grids for id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl**/types**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl/types?id=http://linkedeconomy.org/resource/Subsidy/519339> |
| Get **related projects** of project with id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project.related.projects**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project.related.projects> |
| Get related **decisions** of project with id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project.decisions**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project.decisions> |
| Get related **financial** decisions of project with id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project.decisions.financial**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project.decisions.financial> |
| Get related **non-financial** decisions of project with id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project.decisions.non_financial**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project.decisions.non_financial> |

### API for Model Information
| Action | API Call |
|--------|----------|
| Get a list of all classes, their properties, and property types: | model/classes.tcl<br><http://platform.yourdatastories.eu/api/json-ld/model/classes.tcl> |
| Get a list of all their properties and their types for class **"PublicProject"**:<br>http://linkedeconomy.org/ontology#PublicProject | model/class.tcl, id=...<br><http://platform.yourdatastories.eu/api/json-ld/model/class.tcl?id=http://linkedeconomy.org/ontology%23PublicProject> |
| Get a list of all their properties and their types for class **"Subsidy"**:<br>http://linkedeconomy.org/ontology#Subsidy | model/class.tcl, id=...<br><http://platform.yourdatastories.eu/api/json-ld/model/class.tcl?id=http://linkedeconomy.org/ontology%23Subsidy> |
