# Modules

## Declaring Modules

* Modules with no **keyword declaration**, **imports**, or **exports** will be implicitly assigned to the **global** **module.**
* Modules can be declared with **either** the `module` keyword **or** the `namespace` keyword.

## Extending Modules

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

