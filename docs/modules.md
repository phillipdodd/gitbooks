# Modules

**Modules** are explicitly declared using a **keyword.** 

If **no keyword** is used and there are **no imports** or **exports**, then it will be an **implicit module** assigned to the **global namespace** of **window**. ****This can be thought of as **extending the global namespace.**

```typescript
module dataservice { /* ... */ }
```

### Internal Modules

**Internal Modules** involve being declared using the keyword `namespace`. Within the **namespace**, the `export` keyword is used to make specific things available publicly.

```typescript
namespace Shapes {
    export class Rectangle {
        public height: number;
        public width: number;
        constructor (height: number, width: number) {

        }
    }
}

let myRectangle = new Shapes.Rectangle(2,4);
```

### Internal Interfaces

**Interfaces** are also able to be declared within **modules** in the same way that **classes** are.

{% hint style="info" %}
**Note:** These will be scoped to the module itself and unavailable outside of it.
{% endhint %}

### Extending Modules

Modules can be extended simply by adding things to it later in the code:

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

{% hint style="danger" %}
Though possible, this seems like a **bad practice** to me, as it **harms readability**. Personally, I believe that _should_ a **namespace** need to be extended, it ought to be done so at the **top** of the file or perhaps **as its own, new module.**
{% endhint %}

