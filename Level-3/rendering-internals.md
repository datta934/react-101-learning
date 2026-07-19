<img width="1536" height="1024" alt="rendering-internals" src="https://github.com/user-attachments/assets/429a18f0-a0d8-42af-afb2-486caa0173b0" />

<img width="1024" height="1536" alt="rendering-pipeline" src="https://github.com/user-attachments/assets/6907d3c8-00ae-417d-8099-4ad43bf732e7" />



                Parent renders
                      │
      ┌───────────────┼────────────────┐
      │               │                │
 New Object      New Array      New Function
      │               │                │
      ▼               ▼                ▼
  useMemo        useMemo        useCallback
      │               │                │
      └───────────────┼────────────────┘
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