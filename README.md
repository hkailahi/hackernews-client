A HN client built with ES6 + React.

This app uses the HN Search API provided by Algolia (https://hn.algolia.com/api).


Note:
If you see the following error:
```
Failed to load https://hn.algolia.com/api/v1/search?query=foo&page=0&hitsPerPage=100:
No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin
'http://localhost:3000' is therefore not allowed access. If an opaque response serves
your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled
```

Please change the following in [App component index](/src/components/App/components/index.js)
```javascript
// const proxyurl = "https://cors-anywhere.herokuapp.com/";
const proxyurl = "";
```
to:

```javascript
const proxyurl = "https://cors-anywhere.herokuapp.com/";
// const proxyurl = "";
```

The issue is the [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) implementation from HN Search API, so we must use a proxy to bypass Algolia CORS issues. We can easily host our own instance of [CORS Anywhere](https://github.com/Rob--W/cors-anywhere), a NodeJS proxy which adds CORS headers to the proxied request, to make this work. More information is available [here](https://github.com/Rob--W/cors-anywhere#demo-server).
