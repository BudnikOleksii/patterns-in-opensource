### Builder
З цим паттерном теж працюю часто. Наприклад class QueryBuilder з knex.js чи той же клас обгортка в objection.js. Коли визиваємо метод Model.query() повертається інстанс QueryBuilder і працюємо далі з ним.
Приклад використання:
```javascript
const getUsers = (page, limit) => {
  return User.query()
    .whereNotDeleted()
    .withGraphFetched(TABLES.roles)
    .page(page - 1, limit);
};
```
