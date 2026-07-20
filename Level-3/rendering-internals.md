<img width="1536" height="1024" alt="rendering-internals" src="https://github.com/user-attachments/assets/429a18f0-a0d8-42af-afb2-486caa0173b0" />

<img width="1024" height="1536" alt="rendering-pipeline" src="https://github.com/user-attachments/assets/6907d3c8-00ae-417d-8099-4ad43bf732e7" />




```text
Parent renders
        │
        ▼
Creates Props
        │
        ▼
Objects? Arrays? Functions?
        │
        ▼
New References
        │
        ▼
React.memo
        │
        ▼
Shallow Compare
        │
        ▼
Same Reference?
        │
   ┌────┴────┐
   │         │
  YES       NO
   │         │
   ▼         ▼
Skip Child  Render Child
```


| Situation | React.memo? | Why |
|------------|:----------:|-----|
| Large Table | ✅ Yes | Expensive render |
| Large Dashboard | ✅ Yes | Expensive child components |
| Heavy Charts | ✅ Yes | Rendering cost is high |
| Complex Forms | ✅ Yes | Avoid unnecessary renders |
| Tiny `<Button />` | ❌ Usually No | Rendering is already cheap |
| Tiny `<Title />` | ❌ Usually No | Comparison costs more |
| Component renders rarely | ❌ Usually No | Nothing to optimize |
| Inline Object Props | ❌ Not useful *(unless memoized)* | New object every render |
| Inline Array Props | ❌ Not useful *(unless memoized)* | New array every render |
| Inline Callback Props | ❌ Not useful *(unless memoized)* | New function every render |
| Expensive Custom Comparator | ❌ Usually No | Comparison may cost more than rendering |


| React.memo                        | useMemo                              |
| --------------------------------- | ------------------------------------ |
| Optimizes **component rendering** | Optimizes **expensive calculations** |
| Compares props                    | Compares dependencies                |
| May skip component execution      | May skip recalculating a value       |
| Used around components            | Used inside components               |
| Works well with stable references | Produces stable values/references    |



```                Parent renders
                       │
         ┌─────────────┼─────────────┐
         │                           │
Need stable value?         Need stable function?
         │                           │
         ▼                           ▼
     useMemo                  useCallback
         │                           │
         └─────────────┬─────────────┘
                       │
               Stable References
                       │
                       ▼
                 React.memo
                       │
              Shallow Compare
                       │
                 Same Reference?
                  /          \
                Yes          No
                 │            │
          Skip Child     Render Child
```

![alt text](memo,usememo,callback.png)