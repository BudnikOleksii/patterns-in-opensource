### Adapter
Як казали паттерн костиль.
На проекті коли був інтерном, порадили бібліотеку для 'Soft Delete', яка працює з objection.js ORM, використовув її, але вона не підтримується вже 3 роки, довелося перейти на нову яка була адаптером закинутої бібліотеки. 
Також адаптер можна використовувати якщо змінилось щось в сторонньому API і дані повертаються в іншому форматі. Приклад:
```typescript
import axios from 'axios';

const legacyEndpoint = 'http://legacy-api.com/data';
const newEndpoint = 'http://new-api.com/data';

interface LegacyData {
  firstName: string;
  lastName: string;
  email: string;
}

interface NewData {
  name: string;
  contact: {
    email: string;
  };
}

class LegacyToNewDataAdapter {
  public static adapt(data: LegacyData): NewData {
    return {
      name: `${data.firstName} ${data.lastName}`,
      contact: {
        email: data.email,
      },
    };
  }
}

axios.get<LegacyData>(legacyEndpoint).then((response) => {
  const newData = LegacyToNewDataAdapter.adapt(response.data);
  axios.post<NewData>(newEndpoint, newData);
});
```
