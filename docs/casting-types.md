# Casting Types

**Casting** a value's type using `<...>` notation is a way to 'convert' between types.

To use [Pluralsight](https://app.pluralsight.com/library/courses/typescript/table-of-contents)'s example:

```typescript
//! Fails; createElement returns an HTMLElement
let table: HTMLTableElement = 
    document.createElement('table');

//* Succeeds, uses <>'s to cast the return value's type
let table: HTMLTableElement = 
    <HTMLTableElement>document.createElement('table');
```

