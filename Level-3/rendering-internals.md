## 3.1 to 3.6
<img width="1536" height="1024" alt="rendering-internals" src="https://github.com/user-attachments/assets/429a18f0-a0d8-42af-afb2-486caa0173b0" />

<img width="1024" height="1536" alt="rendering-pipeline" src="https://github.com/user-attachments/assets/6907d3c8-00ae-417d-8099-4ad43bf732e7" />


## 3.7 React.memo 3.8 useMemo 3.9 useCallback

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

<img width="1536" height="1024" alt="memo,usememo,callback" src="https://github.com/user-attachments/assets/3b91c279-8ac4-4eaa-aab2-05a2fc9cfb98" />


---
## 3.10 Rendering Optimization

| Topic               | One-line Memory Trick                  |
| ------------------- | -------------------------------------- |
| Component Splitting | Split by responsibility                |
| State Placement     | Keep state close to where it's used    |
| Composition         | Build complex UIs from simple pieces   |
| Children as JSX     | Let containers render flexible content |
| List Optimization   | Stable keys + minimize work            |
| Virtualization      | Render only what's visible             |
| Lazy Components     | Load UI on demand                      |
| Code Splitting      | Download only what's needed            |
| Dynamic Imports     | Fetch code when required               |

## 3.11 Automatic Batching and 3.12 Concurrent Rendering
<img width="1536" height="1024" alt="3 11and3 12" src="https://github.com/user-attachments/assets/3c11612d-5a33-47bf-9398-0796899bce5d" />

