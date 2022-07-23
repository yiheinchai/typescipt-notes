# Typescript Notes

## slice(1) in Typescript
```ts
type SliceFirst<T extends any[]> = T extends [T[0], ...infer R]: R : never
```

## Use a named variable as property name
```ts
type UseVariable<Key extends string, Value: any> = {[P in Key]: Value} 
```

## Merge intersection types into single object type
```ts
type Combine<T> = {[P in keyof T]: T[P]}
```

## Add additional loop in mapped type by using unions
```ts
type AppendToObject<T, K extends keyof any, V> = {
  [key in keyof T | K]: key extends keyof T ? T[key] : V;
};
```

## Loop over an Array
```ts
type ArrayNumberToString<T extends any[]> = {[P in keyof T]: T[P] extends number ? string : T[P] }
```

## Loop over a Union
```ts
type LoopUnion<Union, Item = Union> = Item extends Item ? `loop ${Item}` : never;
```

## Ensuring Distributed Unions by using Naked Variable left of 'extends'
Conditional types are only distributive when they have the form "T extends ..." (for any type parameter T); a more complex expression left of "extends" does not trigger distributivity.

Not naked (no distribution)
```ts
type LookUp<U extends {type: any}, T> = U['type'] extends T ? U : never
```
Naked (with distribution)
```ts
type LookUp<U, T> = U extends {type: T} ? U : never;
```

## Array type with Mapped Types
```ts
Array<T> = {[K in keyof T]: T[K]}
```

## Never distributed as empty unions
```ts
// when T = never
T extends never = never

// prevent treating never as empty unions
[T] extends [never] = True
```

## Array to Union
```ts
type ArrayToUnion<T extends any[]> = T[number]
type ArrayToUnion<T extends any[]> = T extends (infer U)[] ? U : never
```
