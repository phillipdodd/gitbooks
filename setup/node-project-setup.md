# General Node Project

Cred: [https://developer.okta.com/blog/2018/11/15/node-express-typescript](https://developer.okta.com/blog/2018/11/15/node-express-typescript)

## Install TypeScript and ESLint as Dev Dependencies

```javascript
npm i -D typescript tslint
```

## Installing `.d.ts` files from DefinitelyTyped

Cred: [https://github.com/Microsoft/TypeScript-Node-Starter](https://github.com/Microsoft/TypeScript-Node-Starter)

{% hint style="info" %}
 For the most part, you'll find `.d.ts` files for the libraries you are using on [**DefinitelyTyped**](https://github.com/DefinitelyTyped/DefinitelyTyped/tree/master/types). These `.d.ts` files can be easily installed into your project by using the npm scope `@types`. **For example**, if we want the `.d.ts` file for jQuery, we can do so with 
{% endhint %}

```text
npm install --save-dev @types/jquery
```

**Note**: this will need to be done for _every_ library you're using

## Create tsconfig.json in Project Root

[Link to full documentation](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html)

{% hint style="info" %}
 Based on this `tsconfig.json` file, the TypeScript compiler will \(attempt to\) compile any files ending with `.ts` it finds in the `src` folder, and store the results in a folder named `dist`. Node.js uses the CommonJS module system, so the value for the `module` setting is `commonjs`. Also, the target version of JavaScript is ES6 \(ES2015\), which is compatible with modern versions of Node.js.
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="tsconfig.json" %}
```javascript
{
    "compilerOptions": {
        "module": "commonjs",
        "esModuleInterop": true,
        "target": "es6",
        "noImplicitAny": true,
        "moduleResolution": "node",
        "sourceMap": true,
        "outDir": "dist",
        "baseUrl": ".",
        "paths": {
            "*": [
                "node_modules/*"
            ]
        }
    },
    "include": [
        "src/**/*"
    ]
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Initialize ESLint Settings

[Getting Started with ESLint](https://eslint.org/docs/user-guide/getting-started)  
[Full Configuration Guide](https://eslint.org/docs/user-guide/configuring)

```javascript
./node_modules/.bin/eslint --init
```

This will create an `.eslintrc.json` file in the project's root directory.

{% hint style="info" %}
The value of **eslint:recommended** in the **extends** property contains most common [rules](https://eslint.org/docs/rules/).
{% endhint %}

## Add Build Scripts to package.json

[Intro to NPM Scripts](https://www.freecodecamp.org/news/introduction-to-npm-scripts-1dbb2ae01633/)

{% hint style="info" %}
**NPM Scripts** can be **chained together** **using the `pre` and `post` prefixes**. For example, if you have one script labeled `start` and another labeled `prestart`, executing `npm run start` at the terminal will first run `prestart`, and only after it successfully finishes does `start` run.
{% endhint %}

{% code-tabs %}
{% code-tabs-item title="package.json" %}
```javascript
// ...
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "prebuild": "./node_modules/.bin/eslint .",
    "build": "tsc",
    "prestart": "npm run build",
    "start": "node ."
  }
  // ...
```
{% endcode-tabs-item %}
{% endcode-tabs %}

