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
