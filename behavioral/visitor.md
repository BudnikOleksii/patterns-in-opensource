### Visitor
Не удже з ним розібрався, на реальних прикладах, самий зрозумілий для мене варіант запропонував ChatGPT з бібліотеки D3.js:
```javascript
const svg = d3.select("svg");

const visitor = {
  circle: function(element) {
    element.attr("fill", "blue");
  },
  rect: function(element) {
    element.attr("fill", "red");
  },
  line: function(element) {
    element.attr("stroke", "green");
  }
};

svg.selectAll("*").each(function() {
  const element = d3.select(this);
  const elementType = element.node().nodeName.toLowerCase();
  if (visitor[elementType]) {
    visitor[elementType](element);
  }
});
```
