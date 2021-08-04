# ECMAScript Modules in NodeJS

```js
// typical approach to loading in Express with NodeJS
const express = require('express');
```

```js
// using ES modules:
import express from 'express';
```

Using the ES Modules syntax however can result in the following error message:

```bash
import express from 'express';
^^^^^^

SyntaxError: Cannot use import statement outside a module
```

So how do we fix this? We update our `package.json` file to treat this as a module:

***package.json***
```js
{
  // in the middle, add:
  "type": "module"
}
```

------

## Sources

- [ES6 is the Node way to go](https://dev.to/ibmdeveloper/es6-is-the-node-way-to-go-3715)