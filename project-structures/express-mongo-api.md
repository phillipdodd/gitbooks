# Express - Mongo API



From [https://github.com/Microsoft/TypeScript-Node-Starter](https://github.com/Microsoft/TypeScript-Node-Starter)

* **dist -** Contains the distributable \(or output\) from your TypeScript build. This is the code you ship
* **node\_modules**
* **src -** Contains your source code that will be compiled to the dist dir
  * **config -** Passport authentication strategies and login middleware. Add other complex config code here
  * **controllers -** Controllers define functions that respond to various http requests
  * **lib** - custom modules
  * **routes**
  * **models -** Models define Mongoose schemas that will be used in storing and retrieving data from MongoDB
  * **public** - Static assets that will be used client side
  * **types -** Holds .d.ts files not found on [DefinitelyTyped](https://github.com/DefinitelyTyped/DefinitelyTyped)
  * server.js
* **test -** Contains your tests. Separate from source because there is a different build process.
* **views** - Views define how your app renders on the client
* .env - Used with dotenv
* .travis.yml - Used to configure [Travis CI](https://travis-ci.org/) build
* .copyStaticAssets.ts\* - Build script that copies images, fonts, and JS libs to the dist folder 
* jest.config.js - Used to configure [Jest ](https://jestjs.io/)running tests written in TypeScript
* package.json
* tsconfig.json - Config settings for compiling server code written in TypeScript
* tsconfig.tests.json - Config settings for compiling tests written in TypeScript
* .eslintrc - Config settings for [ESLint ](https://eslint.org/docs/user-guide/command-line-interface)code style checking
* .eslintrcignore - Config settings for paths to exclude from linting

**\*copyStaticAssets.ts** appears to use [shelljs](https://github.com/shelljs/shelljs) to copy the static files over via:

{% code-tabs %}
{% code-tabs-item title="copyStaticAsset.ts" %}
```typescript
import * as shell from "shelljs";

shell.cp("-R", "src/public/js/lib", "dist/public/js/");
shell.cp("-R", "src/public/fonts", "dist/public/");
shell.cp("-R", "src/public/images", "dist/public/");
```
{% endcode-tabs-item %}
{% endcode-tabs %}

