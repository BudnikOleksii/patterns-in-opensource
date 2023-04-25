### Factory Method
Часто стикаємося з даним паттерном, приклад з бібліотеки axios, за допомогою виклика метода create отримуємо новий інстанс axios
```typescript
const $api = axios.create({
  baseURL: API_URL,
});
```

Або в nest.js за допомогою виклика метода create, передаємо наш модуль та отримаємо інстанс
```typescript
async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}

bootstrap();
```
