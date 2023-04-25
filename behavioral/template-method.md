### Template Method
Як приклад компоненти в реакті, ми наслідуємося від Component та перезаписуємо його методи:
```javascript
import React, { Component } from 'react';

class MyComponent extends Component {
  componentDidMount() {}

  componentDidUpdate(prevProps, prevState) {}

  render() {
    return (
      <div>
        <h1>Hello, world!</h1>
        <p>This is my custom component.</p>
      </div>
    );
  }
}
```
