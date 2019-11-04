---
description: My personal style guide
---

# Style Guide

## Functions

* All functions must be written using an **annotation before declaration** approach. This can be done in either of the two methods:

{% tabs %}
{% tab title="With \'Interface\'" %}
```typescript
interface AddTwoInterface {
    (a: number, b: number): number;
}

function addTwo(a, b): AddTwoInterface {
    return a + b;
}
```
{% endtab %}

{% tab title="Without \'Interface\'" %}
```typescript
let addTwo: (a: number, b: number) => number;

addTwo = function (a, b) { 
    return a + b 
}
```
{% endtab %}
{% endtabs %}

* Avoid using arrow functions when defining functions. \(Excludes the arrow-function-like syntax of the 'without interface' approach of annotation\)

## Interfaces

* Interfaces **names** must begin with the letter **I.**

```typescript
interface IDog {
    public breed: string;
    public name?: string;
    public bark: () => string;
}
```

## Classes

* Every class must **implement** an **interface**

```typescript
interface IDog {
    public breed: string;
    public name?: string;
    public bark: () => string;
}

class Dog implements IDog { 
    public breed: string;
    public name: string;
    constructor(breed: string, name?: string) {
        this.breed = breed;
        if (name) {
            this.name = name;
        }
    }
    public bark() {
        return "woof";
    }
}
```

### Class Fields

* When possible, use the `private` or `public` keyword within the **constructor's parameter definitions** to take advantage of Typescript's **auto-declaration** of the **fields** and **auto-assignment** of the **field's values**.
* Class **fields** must be annotated using either the keyword `public` or `private` despite the default being `public`.

{% tabs %}
{% tab title="Good" %}
```typescript
class Rectangle implements IRectangle {

    constructor(
        public height: number,
        public width: number
    ) {}

    public getArea(): number {
        return this.height * this.width;
    }
}
```
{% endtab %}

{% tab title="Bad" %}
```typescript
class Rectangle implements IRectangle {

    height: number;
    width: number;

    constructor(height: number, width: number) {
        this.height = height;
        this.width = width;
    }

    public getArea(): number {
        return this.height * this.width;
    }
}
```
{% endtab %}
{% endtabs %}

## Modules

* Unless having a specific reason to do so, every **module must be declared and named;** Don't rely on on the implicit assignment to the global module.
* Do not **extend** or **add to** a module "later" in the code. Extend modules at the **top of the code only** or consider if a **new module** needs to be created instead.

{% tabs %}
{% tab title="Good" %}
```typescript
namespace Shapes {
    export class Rectangle {
        public height: number;
        public width: number;
        constructor (height: number, width: number) { }
    }
    export class Circle {
        public radius: number;
        constructor(radius: number) {}
    }
}

let myRectangle = new Shapes.Rectangle(2,4);
let myCircle = new Shapes.Circle(20);
```
{% endtab %}

{% tab title="Bad" %}
```typescript
namespace Shapes {
    export class Rectangle {
        public height: number;
        public width: number;
        constructor (height: number, width: number) { }
    }
}

let myRectangle = new Shapes.Rectangle(2,4);

namespace Shapes {
    export class Circle {
        public radius: number;
        constructor(radius: number) {}
    }
}

let myCircle = new Shapes.Circle(20);
```
{% endtab %}
{% endtabs %}

