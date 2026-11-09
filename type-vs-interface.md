# Type Aliases vs. Interfaces in TypeScript

## Introduction

TypeScript uses both `type` aliases and `interface` declarations to describe data shapes. They overlap when defining objects, but each has features suited to different situations.

## Differences and Examples

An `interface` commonly defines an object contract. It supports `extends`, and declarations with the same name can be merged.

```ts
interface Person {
    name: string;
}

interface Employee extends Person {
    employeeId: number;
}
```

A `type` alias can describe an object too, but it can also define unions, tuples, and primitive aliases.

```ts
type Status = "pending" | "approved" | "rejected";

type Coordinates = [number, number];

type Contact = {
    email: string;
};

type StaffContact = Person & Contact;
```

Use `extends` when one interface builds on another. Use `&` when combining types through an intersection. Both can compose object shapes, but only `type` can directly define unions and tuples.

## Conclusion

Choose `interface` for extendable object contracts and declaration merging. Choose `type` when you need unions, tuples, primitive aliases, or intersections. This feature-based rule is more useful than choosing arbitrarily; consistency across a project still matters.