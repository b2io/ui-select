# AngularJS ui-select [![Build Status](https://travis-ci.org/angular-ui/ui-select.svg?branch=master)](https://travis-ci.org/angular-ui/ui-select)

AngularJS-native version of [Select2](http://ivaynberg.github.io/select2/) and [Selectize](http://brianreavis.github.io/selectize.js/).

- [Demo](http://plnkr.co/edit/a3KlK8dKH3wwiiksDSn2?p=preview)
- [Demo Multiselect](http://plnkr.co/edit/juqoNOt1z1Gb349XabQ2?p=preview)
- [Examples](https://github.com/angular-ui/ui-select/blob/master/examples)
- [Documentation](https://github.com/angular-ui/ui-select/wiki)


## Features

- Search, Select, and Multi-select
- Themes: Bootstrap, Select2 and Selectize
- Keyboard support
- jQuery not required (except for old browsers)
- Small code base: 4.57KB min/gzipped vs 20KB for select2

For the roadmap, check [issue #3](https://github.com/angular-ui/ui-select/issues/3) and the [Wiki page](https://github.com/angular-ui/ui-select/wiki/Roadmap).


## Development

### Prepare your environment
* Install [Node.js](http://nodejs.org/) and NPM (should come with)
* Install global dev dependencies: `npm install -g bower gulp`
* Install local dev dependencies: `npm install && bower install` in repository directory

### Development Commands

* `gulp` to jshint, build and test
* `gulp build` to jshint and build
* `gulp test` for one-time test with karma (also build and jshint)
* `gulp watch` to watch src files to jshin, build and test when changed

## Contributing

- Run the tests
- Try the [examples](https://github.com/angular-ui/ui-select/blob/master/examples)

When issuing a pull request, please exclude changes from the "dist" folder to avoid merge conflicts.


## Custom Additions
- Works in ie8
- Added spinner for select2 theme when refreshing data
  - return a promise in your `refresh` methods
  - disable with `refreshSpinner="false"`

Spinner Code Example
```
<div ui-select-choices repeat="obj in data" refresh="refreshData($select.search)">
  <div ng-bind-html="obj.displayName | highlight:$select.search"></div>
</div>

function refreshUsers(searchTerm) {
    return DataService.getData(searchTerm).then(function(newData) {
        $scope.data = newData;
    }
}
```
Note: `DataService.getData()` is returning a promise (`$q.defer()`).

