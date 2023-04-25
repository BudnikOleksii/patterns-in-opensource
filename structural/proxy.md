### Proxy
Axios пропонує proxy.
```javascript
const proxyConfig = {
  host: 'localhost',
  port: 8080,
};

const axiosProxy = axios.create({
  proxy: proxyConfig,
});
```
