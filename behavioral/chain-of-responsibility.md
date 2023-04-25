### Chain of Responsibility
Кожен день працюю з даним патерном, всі middlewares виконують свою роботу і передають по ланцюжку далі, приклад використання з express.js
```javascript
const path = require('path');
const express = require('express');
const cors = require('cors');
const morgan = require('morgan');

const api = require('./routes/api');
const { apiEntrypoint, corsOptions } = require('../config').server;
const { errorHandler } = require('./middlewares/error-handler');

const app = express();

app.use(cors(corsOptions));
app.use(morgan('combined'));
app.use(express.json());
app.use(express.static(path.join(__dirname, '..', 'public')));
api.use(errorHandler);
app.use(apiEntrypoint, api);
```
