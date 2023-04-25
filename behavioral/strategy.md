### Strategy
Приклад реалізації стратегії з бібліотеки validator.js:
```typescript
interface ValidationStrategy {
  validate(value: any): boolean;
}

class EmailValidationStrategy implements ValidationStrategy {
  validate(value: any): boolean {
    return validator.isEmail(value);
  }
}

class MinLengthValidationStrategy implements ValidationStrategy {
  constructor(private minLength: number) {}

  validate(value: any): boolean {
    return validator.isLength(value, { min: this.minLength });
  }
}

class Validator {
  constructor(private strategy: ValidationStrategy) {}

  setStrategy(strategy: ValidationStrategy) {
    this.strategy = strategy;
  }

  validate(value: any): boolean {
    return this.strategy.validate(value);
  }
}

const emailValidator = new Validator(new EmailValidationStrategy());
const minLengthValidator = new Validator(new MinLengthValidationStrategy(8))
```
