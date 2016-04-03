---
title: 'JSON-LD API'
---

This section provides some examples regarding the [JSON-LD](http://json-ld.org/) API.


| Action (Grid Component) | API Call |
|-------------------------|----------|
| Get project with id (**Greek**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=el**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http%3A%2F%2Flinkedeconomy.org%2Fresource%2FSubsidy%2F519339&type=project&lang=el> |
| Get project with id (**English**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=en**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project&lang=en> |
| Get project with id (**all available languages**): http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project**, **lang=i18n**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project&lang=i18n> |
| Get types (facets) supported for id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl**/types**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl/types?id=http://linkedeconomy.org/resource/Subsidy/519339> |
| Get related projects of project with id: http://linkedeconomy.org/resource/Subsidy/519339 | component/grid.tcl, **type=project.related.projects**, id=...<br><http://platform.yourdatastories.eu/api/json-ld/component/grid.tcl?id=http://linkedeconomy.org/resource/Subsidy/519339&type=project.related.projects> |
