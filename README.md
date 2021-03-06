[![Build Status](https://travis-ci.org/andrefarzat/ng-jcrop.svg?branch=master)](https://travis-ci.org/andrefarzat/ng-jcrop)
[![Coverage Status](https://coveralls.io/repos/andrefarzat/ng-jcrop/badge.png)](https://coveralls.io/r/andrefarzat/ng-jcrop)
[![Code Climate](https://codeclimate.com/github/andrefarzat/ng-jcrop/badges/gpa.svg)](https://codeclimate.com/github/andrefarzat/ng-jcrop)
[![David dm](https://david-dm.org/andrefarzat/ng-jcrop.svg)](https://david-dm.org/andrefarzat/ng-jcrop)

ng-jcrop
========

Angular directive to jCrop jQuery plugin


### Demo

http://andrefarzat.github.io/ng-jcrop/


### Installing

Install via `bower` or `npm`

```sh
bower install ng-jcrop --save
# or
npm install ng-jcrop --save
```


It depends of angular, jquery and jquery-jcrop, so it is necessary including all libraries

```html
<link rel="stylesheet" href="bower_components/jcrop/css/jquery.Jcrop.css" />

<script src="bower_components/jquery/dist/jquery.js"></script>
<script src="bower_components/jcrop/js/jquery.Jcrop.js"></script>
<script src="bower_components/angular/angular.js"></script>
<script src="bower_components/ng-jcrop/ng-jcrop.js"></script>
```

### Usage

```js
// add 'ngJcrop' as dependency to your module
var yourModule = angular.module("yourModule", ['ngJcrop']);
```

And add the `ng-jcrop` directive in an `<div>` giving the
image's src as the value
```html
<script>

var app = angular.module('yourModule', ['ngJcrop']);

// Optional configuration via ngJcropConfigProvider
app.config(function(ngJcropConfigProvider){

    // [optional] To change the jcrop configuration
    // All jcrop settings are in: http://deepliquid.com/content/Jcrop_Manual.html#Setting_Options
    ngJcropConfigProvider.setJcropConfig({
        bgColor: 'black',
        bgOpacity: .4,
        aspectRatio: 16 / 9
    });

    // [optional] To change the css style in the preview image
    ngJcropConfigProvider.setPreviewStyle({
        'width': '100px',
        'height': '100px',
        'overflow': 'hidden',
        'margin-left': '5px'
    });

});

app.controller('SomeController', function($scope){
    $scope.obj = {}

    // The url or the data64 for the image
    $scope.obj.src = 'beautifulImage.jpg';

    // Must be [x, y, x2, y2, w, h]
    $scope.obj.coords = [100, 100, 200, 200, 100, 100];

    // You can add a thumbnail if you want
    $scope.obj.thumbnail = true;
});
</script>


<div ng-jcrop="obj.src" selection="obj.coords" thumbnail="obj.thumbnail"></div>
````

### Testing

It is necessary install `karma` and its dependencies
```shell
npm install
```

Then you can run the tests
```shell
npm test
```


### Starting the demo page

It is necessary install the `http-server`
```shell
npm install
```

Then you run `npm run serve` and access [`http://localhost:8080/demo`](http://localhost:8080/demo)
