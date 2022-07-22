# Typescript Notes

## slice(1) in Typescript
```
type SliceFirst<T extends any[]> = T extends [T[0], ...infer R]: R : never
```
