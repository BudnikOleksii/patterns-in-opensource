### Prototype
Як я зрозумів є достатньо готових реалізацій даного паттерна, наприклад бібліотека clone.
```javascript
const clone = require('clone');

const user = {
  name: 'Oleksii Budnik',
  age: 30,
  address: {
    city: 'Kyiv',
    state: 'Kyiv',
    country: 'Ukraine'
  }
};

const clonedUser = clone(user);
```
