# Type Narrowing in TypeScript

## Introduction

Type narrowing allows TypeScript to treat a value as a more specific type after a check. It is useful with union types because different operations are valid for different members.

## Main Techniques

**1. `typeof`**

Use `typeof` to check primitive values such as strings and numbers.

```ts
function describe(value: string | number): string {
    if (typeof value === "string") {
        return value.toUpperCase();
    }
    return value.toFixed(2);
}
```

**2. The `in` operator**

Use `in` to check whether an object contains a property. TypeScript then narrows the object to the type that declares that property.

```ts
type Admin = { permissions: string[] };
type User = { username: string };

function getRole(person: Admin | User): string {
    if ("permissions" in person) {
        return "Admin";
    }
    return "User";
}
```

**3. `instanceof`**

Use `instanceof` to check whether an object was created from a particular class.

```ts
class Car {
    start(): string {
        return "Started";
    }
}

function startVehicle(vehicle: Car | Date): string {
    if (vehicle instanceof Car) {
        return vehicle.start();
    }
    return vehicle.toDateString();
}
```

A truthiness check can also narrow values, but it treats `""` and `0` as falsy. If either is a valid value, use an explicit comparison instead.

## Conclusion

These checks help TypeScript identify which operations are safe. Choosing the appropriate check makes code clearer and reduces errors when handling union types.