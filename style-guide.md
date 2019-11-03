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
    (a: number, b:number): number;
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

## Classes

* Class **fields** must be explicity annotated at the top of the class definition; don't rely on the constructor parameters to auto-create them for you.

{% tabs %}
{% tab title="Good" %}
```typescript
class Dog {
    breed: string;
    constructor(breed: string) {
        this.breed = breed;
    }
}
```
{% endtab %}

{% tab title="Bad" %}
```typescript
class Dog {
    constructor (public breed: string) {
        this.breed = breed;
    }
}
```
{% endtab %}
{% endtabs %}

* Every class must **implement** an **interface**

```typescript
interface IDog {
    breed: string;
    name?: string;
    bark: () => string;
}

class Dog implements IDog { 
    breed: string;
    name: string;
    constructor(breed: string, name?: string) {
        this.breed = breed;
        if (name) {
            this.name = name;
        }
    }
    bark() {
        return "woof";
    }
}
```

