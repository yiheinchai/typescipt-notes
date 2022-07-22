# Typescript Notes

## slice(1) in Typescript
```tsx
type SliceFirst<T extends any[]> = T extends [T[0], ...infer R]: R : never
```

## Use a named variable as property name
type UseVariable<Key extends string, Value: any> = {[P in Key]: Value} 
