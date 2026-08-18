## 13.1 TS Fundamentals
| Concept     | Remember                  |
| ----------- | ------------------------- |
| `interface` | Object contract           |
| `type`      | Flexible type composition |
| `\|`        | OR / union                |
| `&`         | AND / intersection        |
| `any`       | Disables safety           |
| `unknown`   | Safe unknown              |
| `never`     | Impossible/no return      |
| `?`         | Property may be missing   |
| `null`      | Explicitly no value       |
| `as`        | Compile-time assertion    |
| Type guard  | Narrows type              |
| `keyof`     | Gets keys                 |
| `typeof`    | Gets type from value      |
| `as const`  | Literal + readonly        |


## 13.2 React + TypeScript
<img width="1024" height="1536" alt="13 2" src="https://github.com/user-attachments/assets/a66d9ebb-2aac-4126-8cc9-14a22ca3128c" />

## 13.3 Generics
Generics = reusable code + preserved type information.

Generics allow us to write reusable, type-safe code that works with different types while preserving the relationship between those types.

`any` removes type safety. Generics preserve the actual type information and allow TypeScript to validate how the value is used.

generics in React? - They're especially useful for reusable components, hooks, API abstractions, tables, lists, selects, and design-system components where the same component needs to work with different data types while remaining type-safe.

| Syntax              | Meaning                  |
| ------------------- | ------------------------ |
| `<T>`               | Generic type parameter   |
| `T`                 | Placeholder for a type   |
| `<T, U>`            | Multiple type parameters |
| `T extends X`       | T must satisfy X         |
| `keyof T`           | Keys of T                |
| `K extends keyof T` | K must be a key of T     |
| `T[K]`              | Type of property K       |
| `ApiResponse<T>`    | Generic interface        |
| `List<T>`           | Generic component        |
| `useFetch<T>`       | Generic hook             |
