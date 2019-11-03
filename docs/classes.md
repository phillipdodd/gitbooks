# Classes

Classes in Typescript are comprised of four things:

* Fields
* Constructor
* Properties
* Functions

## Fields and Constructors

```typescript
class Dog {

    //* Field Declaration
    breed: string;

    //* Used to initialize field(s)
    //! Not required if init not needed
    constructor(breed: string) {
        this.breed = breed;
    }

}
```

Alternatively, the keywords **public** or **private** can be used to declare a field within the constructor's parameters:

{% hint style="warning" %}
All **fields** are **public** by **default** unless specifically declared as **private**.
{% endhint %}

```typescript
class Dog {
    constructor(public breed: string) {
        this.breed = breed;
    }
}
```

{% hint style="success" %}
At the current time, the **first example** seems the **more appealing** one. The first feels **more readable**, not being a "shorthand".
{% endhint %}

## Properties

**Properties** wrap **fields** and can provide **getters** and **setters** for that field, allowing for custom operations or data filtering.

```typescript
class Dog {

    private _breed: string;
    
    public get breed(): string {
        return this._breed;
    }

    public set breed(value: string) {
        this._breed = value;
    }

    constructor(breed: string) {
        this.breed = breed;
    }

}
```

{% hint style="info" %}
**Getters** and **Setters** are **also available** to vanilla Javascript objects; they are not a Typescript-specific feature. See the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects) for more information.
{% endhint %}

## Extending a Class / Type

To create a child class or type, or extension, the **extends** keyword and **super\(\)** constructor must be used like so:

```typescript
class ChildClass extends ParentClass {
    constructor() {
        super();
    }
}
```

`super()` calls the **parent's constructor.** Any necessary parameters will need to be passed through that the parent's constructor is expecting.

```typescript
class Animal {
    isCute: boolean;
    constructor(isCute: boolean) {
        this.isCute = isCute;
    }
}

class Dog extends Animal {
    breed: string;
    constructor(isCute: boolean, breed?: string) {
        super(isCute);
        if (breed) { 
            this.breed = breed;
        }
    }
}
```

## Using Interfaces

To apply an **interface** to a **class,** the **implements** keyword is used.

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

This may not _look_ that much different, but what it accomplishes is that it provides an **easily-readable guarantee** that the class is going to return a specific _kind_ of object. 

{% hint style="info" %}
Additionally, **interfaces** can be used when defining field's **types**
{% endhint %}

