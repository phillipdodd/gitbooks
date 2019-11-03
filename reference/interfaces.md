# Interfaces

**Interfaces** can be used to describe both **functions** and **objects.** 

By convention, they are named starting with the letter **I.**

**They can be extended like classes!**

See **Grammar** page linked below for more information.

{% page-ref page="../docs/grammar.md" %}

## Function Interfaces

```typescript
interface IAddTwoInterface {
    (a: number, b:number): number;
}

const addTwo: IAddTwoInterface = (a, b) => a + b;

//* Or...
function addTwo(a, b): IAddTwoInterface {
    return a + b;
}
```

## Object Interfaces

```typescript
interface IDog {
    breed: string;
    name?: string;
    bark: () => string;
}

let myDog: IDog = {
    breed: "doggo",
    bark: () => "woof!"
}

let myOtherDog: IDog = {
    breed: "pupper",
    name: "bob",
    bark: () => "yip!"
}
```

## Class Implementing Interfaces

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

## Extending Interfaces

```typescript
interface IAnimal {
    isCute: boolean;
}

interface IDog extends IAnimal {
    isPupper: boolean;
}

class Dog implements IDog { 
    isCute: boolean;
    isPupper: boolean;
    constructor(isCute: boolean, isPupper: boolean) {
        this.isCute = isCute;
        this.isPupper = isPupper;
    }
}

let myDog = new Dog(true, true);
```

