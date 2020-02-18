# Jest

## Config
```
"env": {
  "jest": true
}
```
The above code should be added to "eslintConfig" from `package.json`, `.eslintrc`, or the equivalent config file when using Jest. Otherwise `describe`, `it`, or other common functions in Jest would appeared undefined.

```
{
  "presets": [
    ["@babel/preset-env",
      { "targets": { "node": "current"
        }
      }],
    "@babel/preset-react"
  ]
}
```
Add the above code to `.babelrc` file and replace the plugin `@babel/plugin-transform-react-jsx`. Since JSX isn't actually JavaScript, when testing snapshot, Jest will throw a "unexpected token" error. It must be compiled into `React.createElement` calls, which is done by Babel plugin `@babel/plugin-transform-react-jsx`, which itself is included as part of `@babel/preset-react`.

If you are using `@babel/preset-env` but without the target set, this will result in the test using async failing with `ReferenceError: regeneratorRuntime is not defined` error. Note that `babel-polyfill` mentioned by some other solutions is deprecated.

## Testing Endpoints
Install Supertest in order to test endpoints.

Note that for this to work, the server file cannot listen to a port, otherwise you will get the error stating that "port in use". You want to allow each test file to start a server on their own. To achieve this, instead of having express listen to port 3000 at the end, export express app without listening.
```
// index.js
const express = require('express');
const app = express();

// ...

// app.listen(3000); // Don't listen to a port here
module.exports = app;
```

For development or production purposes, listen to the port in a different file.
```
// start.js
const app = require('./index');
app.listen(3000);
```

Require the express app and supertest in the test file when using supertest.
```
const app = require('./index');
const supertest = require('supertest');
const request = supertest(app);
```

Check *Ascend* for sample test file for different endpoints.

## Resource
- [Jest Documentation](https://jestjs.io/docs/en/getting-started.html)
- [Supertest Documentation](https://github.com/visionmedia/supertest)

[Back](../../README.md)
