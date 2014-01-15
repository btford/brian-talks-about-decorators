# Decorators in AngularJS

A lightning talk about decorating services with Angular's DI.

First, monkey patching in JS:

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

Using this technique, you can augment the behavior of `someFunction`.

Next, here's how you can get an Angular service as its being instantiated:

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

Using these two techniques together, you can patch all sorts of things for great justice.

With great power comes responsibility.

## Example
See `index.html` for an example.

## License
MIT
