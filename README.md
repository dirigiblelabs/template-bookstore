# Template V3 - Bookstore

[![Eclipse License](http://img.shields.io/badge/license-Eclipse-brightgreen.svg)](LICENSE)
[![GitHub contributors](https://img.shields.io/github/contributors/dirigiblelabs/template-v3-bookstore.svg)](https://github.com/dirigiblelabs/template-v3-bookstore/graphs/contributors)


## Overview

Simple vertical Bookstore application with a database table definiton, a server-side scripting service and user interface in HTML5 with Bootstrap & AngularJS.

- Database table definition:

```javascript
{
"name":"{{fileName}}_BOOKS",
"type": "TABLE",
"columns":
[
  {
    "name":"BOOK_ID",
    "type":"INTEGER",
    "length":"0",
    "nullable":"false",
    "primaryKey":"true",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_ISBN",
    "type":"CHAR",
    "length":"13",
    "nullable":"false",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_TITLE",
    "type":"VARCHAR",
    "length":"200",
    "nullable":"false",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_AUTHOR",
    "type":"VARCHAR",
    "length":"100",
    "nullable":"false",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_EDITOR",
    "type":"VARCHAR",
    "length":"100",
    "nullable":"true",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_PUBLISHER",
    "type":"VARCHAR",
    "length":"100",
    "nullable":"true",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_FORMAT",
    "type":"VARCHAR",
    "length":"100",
    "nullable":"true",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_PUBLICATION_DATE",
    "type":"DATE",
    "length":"0",
    "nullable":"true",
    "primaryKey":"false",
    "defaultValue":""
  }
  ,
  {
    "name":"BOOK_PRICE",
    "type":"DOUBLE",
    "length":"0",
    "nullable":"true",
    "primaryKey":"false",
    "defaultValue":""
  }
]
}
```

- Scripting service in Javascript

```javascript
var rsdata = require('http/v3/rs-data'); 

rsdata
  .service()
    .dao({
	  "table": "{{fileName}}_BOOKS",
	  "properties": [{
		  	"name": "id",
	    	"column": "BOOK_ID",
			"type":"INTEGER",
			"id": true,
			"required": true
		}, {
			"name": "isbn",
		    "column":"BOOK_ISBN",
		    "type":"CHAR",
		    "size": 13,
		    "required": true
		}, {
			"name": "title",
			"column":"BOOK_TITLE",
			"type":"VARCHAR",
			"size":"200",
			"required": true
		}, {
			"name": "author",
			"column":"BOOK_AUTHOR",
			"type":"VARCHAR",
			"size": 100,
			"required": true
		}, {
			"name": "editor",
			"column":"BOOK_EDITOR",
			"type":"VARCHAR",
			"size": 100
		}, {
			"name": "publisher",
			"column":"BOOK_PUBLISHER",
			"type":"VARCHAR",
			"length": 100
		}, {
			"name": "format",
			"column":"BOOK_FORMAT",
			"type":"VARCHAR",
			"length": 100
		}, {
			"name": "publication_date",
			"column":"BOOK_PUBLICATION_DATE",
			"type":"DATE"
		}, {
			"name": "price",
			"column":"BOOK_PRICE",
			"type":"DOUBLE"
		}]
    })
  .execute();
```

- User interface in HTML5

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

    <div>
      <div class="page-header">
        <h1>[[fileName]] Books</h1>
      </div>
      <div class="container">
        <table class="table table-hover">
          <thead>
            <th>#</th>
            <th>ISBN</th>
            <th>Title</th>
            <th>Author</th>
            <th>Editor</th>
            <th>Publisher</th>
            <th>Format</th>
            <th>Publication Date</th>
            <th>Price</th>
          </thead>
          <tbody>
            <tr ng-repeat="book in books">
              <td>{{book.id}}</td>
              <td>{{book.isbn}}</td>
              <td>{{book.title}}</td>
              <td>{{book.author}}</td>
              <td>{{book.editor}}</td>
              <td>{{book.publisher}}</td>
              <td>{{book.format}}</td>
              <td>{{book.publication_date}}</td>
              <td>{{book.price}}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>

    <script type="text/javascript">
      angular.module('page', []);
      angular.module('page').controller('PageController', function ($scope, $http) {

        $http.get('../../js/[[projectName]]/[[fileName]].js')
        .success(function(data) {
        	$scope.books = data;
        });

  	  });
    </script>
  </body>
</html>
```


## License

This project is copyrighted by [SAP SE](http://www.sap.com/) and is available under the [Eclipse Public License v 1.0](https://www.eclipse.org/legal/epl-v10.html). See [LICENSE](LICENSE) and [NOTICE.txt](NOTICE.txt) for further details.
