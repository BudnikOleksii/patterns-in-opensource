### Iterator
Можливо я не правильно зрозумів, але функції генератори реалізують даний патерн.
```javascript
function* numberSequence() {
  let i = 1;
  while (true) {
    yield i++;
  }
}

const sequence = numberSequence();
console.log(sequence.next().value); // 1
console.log(sequence.next().value); // 2
console.log(sequence.next().value); // 3
```

