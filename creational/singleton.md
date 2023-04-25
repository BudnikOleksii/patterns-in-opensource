### Singleton
Приклад використання з typeorm.
```typescript
import { Connection, createConnection } from 'typeorm';

class Database {
  private static instance: Database;
  private connection: Connection;

  private constructor() {}

  public static getInstance(): Database {
    if (!Database.instance) {
      Database.instance = new Database();
      Database.instance.connection = createConnection();
    }

    return Database.instance;
  }

  public getConnection(): Connection {
    return this.connection;
  }
}

const dbInstance1 = Database.getInstance();
const dbInstance2 = Database.getInstance();

console.log(dbInstance1 === dbInstance2);
```
