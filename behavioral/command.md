### Command
Як простий приклад, використовуємо даний паттерн в redux:
```javascript
import { createAction } from '@reduxjs/toolkit';

const incrementCounter = createAction('INCREMENT_COUNTER');
const decrementCounter = createAction('DECREMENT_COUNTER');

const counterReducer = (state = { value: 0 }, action) => {
  switch (action.type) {
    case incrementCounter.type:
      return { ...state, value: state.value + 1 };
    case decrementCounter.type:
      return { ...state, value: state.value - 1 };
    default:
      return state;
  }
};

const store = createStore(counterReducer);

store.dispatch(incrementCounter());
store.dispatch(decrementCounter());
```
