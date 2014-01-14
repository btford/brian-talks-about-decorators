# Decorators in AngularJS

A lightning talk about decorating services with Angular's DI.

Monkey patching in JS:

```javascript
function someFunction () { /* ... */ }

var originalFunction = someFunction;
function wrapperFunction () {
  // do stuff before the original function
  var returnValue = originalFunction.apply(this, arguments);
  // do stuff after the original function
  return returnValue;
}

someFunction = wrapperFunction;
```

Here's how you can get ahold of an Angular service as its being instantiated:

```javascript
angular.module('ng')
  .config(function ($provide) {
    // in this case, we're grabbing $rootScope, so $delegate == $rootScope
    $provide.decorator('$rootScope', function ($delegate) {
      // do whatever you you want
      return $delegate;
    });
  });
```

## Example
See `index.html` for an example.

## License
MIT
