## How to setup path alias Javascript in VSCode?

Problem: a lot **_../_** using **require** or **import** in Javascript

```js
const { DoSomething } = require("../../lib/do-something");
```

... happy with that

```js
const { DoSomething } = require("@lib/do-something");
```

> Fun fact: Typescript is navite support path alias and you just setup with file **tsconfig.json** and VSCode support also.

## How about with JavaScript?

Using package [module-alias](https://github.com/ilearnio/module-alias)

1. Install package

```sh
npm install module-alias
```

2. Setup path alias in file package.json

```json
{
  "name": "path_alias",
  "version": "1.0.0",
  "description": "Setup path alias with Javascript",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "module-alias": "^2.2.2"
  },
  "_moduleAliases": {
    "@api": "./api",
    "@lib": "./lib"
  }
}
```

3. Require package in top of the main file (index.js) before any code.

```js
require("module-alias/register");
```

TADA
Now you can running your code without error
![wth](/images/tada.png)

**Hold on, but you can go to define in VSCode**

![wth](/images/wth.jpg)

Let try with file **jsconfig.json** and enjoy

```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./*"],
      "@api/*": ["./api/*"],
      "@lib/*": ["./lib/*"]
    }
  }
}
```
