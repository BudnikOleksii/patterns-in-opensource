### Decorator
Як приклад часто використовувал debounce, і з бібліотек lodash, MUI чи вручну писав.
```javascript
const debounce = (fn, delay) => {
  let timeoutId;

  return function(...args) {
    clearTimeout(timeoutId);

    timeoutId = setTimeout(() => {
      fn.apply(this, args);
    }, delay);
  };
}
```
