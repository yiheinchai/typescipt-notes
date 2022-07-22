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

## Loop over an Array
```ts
type ArrayNumberToString<T extends any[]> = {[P in keyof T]: T[P] extends number ? string : T[P] }
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
