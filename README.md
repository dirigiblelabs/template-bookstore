# Template V3 - HTML

[![Eclipse License](http://img.shields.io/badge/license-Eclipse-brightgreen.svg)](LICENSE)
[![GitHub contributors](https://img.shields.io/github/contributors/dirigiblelabs/template-v3-html.svg)](https://github.com/dirigiblelabs/template-v3-html/graphs/contributors)


## Overview

Simple "HTML" page with Bootstrap & AngularJS
```html
<!DOCTYPE html>
<html lang="en" ng-app="page">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="">
    <meta name="author" content="">

    <link type="text/css" rel="stylesheet" href="/services/v3/core/theme/bootstrap.min.css">
    <link type="text/css" rel="stylesheet" href="/services/v3/web/resources/font-awesome-4.7.0/css/font-awesome.min.css">

    <script type="text/javascript" src="/services/v3/web/resources/angular/1.4.7/angular.min.js"></script>
    <script type="text/javascript" src="/services/v3/web/resources/angular/1.4.7/angular-resource.min.js"></script>
  </head>

  <body ng-controller="PageController">
    <div class="form-group">
      <label>Explore:</label>
      <select class="form-control" ng-model="explore">
        <option value="customers">Customers</option>
        <option value="employees">Employees</option>
        <option value="products">Products</option>
      </select>
    </div>
    ...
```


## License

This project is copyrighted by [SAP SE](http://www.sap.com/) and is available under the [Eclipse Public License v 1.0](https://www.eclipse.org/legal/epl-v10.html). See [LICENSE](LICENSE) and [NOTICE.txt](NOTICE.txt) for further details.
