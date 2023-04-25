### Abstract Factory
З цим паттерном напряму не стикався здається, попитав трохи ChatGPT. Один з запропонованих прикладів з typeorm, interface DatabaseDriver.
Інтерфейс DatabaseDriver представляє собой абстрактну фабрику, а класи `PostgresDriverFactory`, `MysqlDriverFactory` та `SqliteDriverFactory` презентують фабрики для конкретних баз даних імплементуючи даний інтерфейс.
```typescript
interface DatabaseDriver {
  connect(options: ConnectionOptions): Promise<void>;
  disconnect(): Promise<void>;
}

interface DatabaseDriverFactory {
  createDriver(options: ConnectionOptions): DatabaseDriver;
}

class PostgresDriverFactory implements DatabaseDriverFactory {
  createDriver(options: ConnectionOptions): DatabaseDriver {
    return new PostgresDriver();
  }
}

class MysqlDriverFactory implements DatabaseDriverFactory {
  createDriver(options: ConnectionOptions): DatabaseDriver {
    return new MysqlDriver();
  }
}

class SqliteDriverFactory implements DatabaseDriverFactory {
  createDriver(options: ConnectionOptions): DatabaseDriver {
    return new SqliteDriver();
  }
}

class DatabaseConnector {
  private driverFactory: DatabaseDriverFactory;

  constructor(driverFactory: DatabaseDriverFactory) {
    this.driverFactory = driverFactory;
  }

  async connect(options: ConnectionOptions): Promise<void> {
    const driver = this.driverFactory.createDriver(options);
    await driver.connect(options);
  }

  async disconnect(): Promise<void> {
    // ...
  }
}
```
