## 5.1 Fetch API - 5.2 Axios - 5.3 React Query (TanStack Query) - 5.4 SWR

```
Backend
    │
    ▼
Fetch / Axios
    │
    ▼
─────────────────────────────
│                           │
▼                           ▼
React Query              SWR
│
▼
Cache
Retry
Refetch
Mutations
─────────────────────────────
│
▼
Redux?
│
├── Yes → RTK Query
└── No  → React Query / SWR
```

```
                    LEVEL 5 — DATA FETCHING

┌─────────────────────┬──────────────────────┬──────────────────────┬──────────────────────┐
│       FETCH         │        AXIOS         │     REACT QUERY      │         SWR          │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Goal                │ Goal                 │ Goal                 │ Goal                 │
│ Native HTTP Client  │ Enterprise HTTP      │ Server State Manager │ Simple Server State  │
│                     │ Client               │                      │ (Next.js friendly)   │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Responsible For     │ Responsible For      │ Responsible For      │ Responsible For      │
│ Sending Requests    │ Sending Requests     │ Managing Server Data │ Managing Server Data │
│                     │                      │                      │                      │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Think As            │ Think As             │ Think As             │ Think As             │
│ Bicycle             │ Car                  │ Fleet Manager        │ Scooter              │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Example             │ Example              │ Example              │ Example              │
│ fetch('/products')  │ api.get('/products') │ useQuery(...)        │ useSWR(...)          │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Best For            │ Best For             │ Best For             │ Best For             │
│ Small Apps          │ Enterprise Apps      │ React Apps           │ Next.js Sites        │
│ Few APIs            │ Auth                 │ Zustand/Context      │ Dashboards           │
│                     │ Logging              │ Large CRUD           │ Blogs                │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Built-in Cache      │ Built-in Cache       │ Built-in Cache       │ Built-in Cache       │
│ ❌                  │ ❌                   │ ✅                   │ ✅                   │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Interceptors        │ Interceptors         │ Interceptors         │ Interceptors         │
│ ❌                  │ ✅                   │ Uses Axios/Fetch     │ Uses Axios/Fetch     │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Loading/Error       │ Loading/Error        │ Loading/Error        │ Loading/Error        │
│ Manual              │ Easier              │ Automatic            │ Automatic            │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Retry               │ Retry                │ Retry                │ Retry                │
│ Manual              │ Manual              │ ✅                   │ ✅                   │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Background Refetch  │ Background Refetch   │ Background Refetch   │ Background Refetch   │
│ ❌                  │ ❌                   │ ✅                   │ ✅                   │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Common Misconception│ Common Misconception │ Common Misconception │ Common Misconception │
│ "Fetch handles      │ "Axios replaces      │ "React Query         │ "Only Next.js        │
│ HTTP errors." ❌     │ React Query." ❌     │ replaces Axios." ❌   │ can use SWR." ❌      │
│ Check response.ok   │ It only replaces     │ It sits above        │ It works with any    │
│                     │ Fetch                │ Axios/Fetch          │ React app            │
├─────────────────────┼──────────────────────┼──────────────────────┼──────────────────────┤
│ Key API             │ Key API              │ Key API              │ Key API              │
│ fetch()             │ axios.create()       │ QueryClient          │ useSWR()             │
│ AbortController     │ Interceptors         │ useQuery()           │ mutate()             │
│                     │                      │ useMutation()        │                      │
└─────────────────────┴──────────────────────┴──────────────────────┴──────────────────────┘
```

## 5.5 - 5.8
```
Backend
    │
    ▼
HTTP Client (Fetch / Axios)
    │
    ▼
Server State Library
(RTK Query / React Query / SWR)
    │
    ▼
Cache
    │
    ├── Background Refetch
    ├── Stale While Revalidate
    ├── Optimistic Updates
    ├── Infinite Queries
    └── Pagination
```