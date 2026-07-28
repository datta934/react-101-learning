## 10.1 Application Architecture
| Topic                       | One-line Definition                         | Best Practice                               | Interview Tip                    |
| --------------------------- | ------------------------------------------- | ------------------------------------------- | -------------------------------- |
| Layer Architecture          | Organize by file type                       | Good for small apps                         | Doesn't scale well               |
| Feature Architecture        | Organize by business feature                | ⭐ Best for enterprise                       | Most common React architecture   |
| Clean Architecture          | Separate UI, business logic & data          | UI shouldn't know API details               | Dependency flows downward        |
| Enterprise Folder Structure | Organize by ownership                       | `app`, `features`, `shared`, `services`     | Makes ownership obvious          |
| Shared Folder               | Reusable across features                    | Keep it small                               | Don't dump everything here       |
| Feature Folder              | Contains everything for one business domain | Components, hooks, services, tests together | Easier onboarding                |
| Service/Repository Layer    | Handles API communication                   | UI → Service → Repository → API             | Easy to swap Axios/Fetch         |
| Scalability                 | Design for future growth                    | Prefer Feature Architecture                 | Think about 50 developers, not 5 |

| Situation              | Choose                       |
| ---------------------- | ---------------------------- |
| Small App (5–10 pages) | Layer Architecture           |
| Medium App             | Feature Architecture         |
| Enterprise App         | Feature + Clean Architecture |
| Multiple Teams         | Feature Ownership            |


## 10.2 Component Architecture and 10.3 Design System Architecture
| Topic                    | One-line Definition                        | Best Practice                      | Interview Tip                        |
| ------------------------ | ------------------------------------------ | ---------------------------------- | ------------------------------------ |
| Presentational Component | UI only                                    | No API/business logic              | Focus on rendering                   |
| Container Component      | Handles data & state                       | Fetch data, pass props             | Often replaced by custom hooks today |
| Composition              | Build components by combining smaller ones | Prefer over inheritance            | React's recommended approach         |
| Compound Components      | Parent controls related child components   | `<Modal.Header />`                 | Flexible and clean APIs              |
| Design System            | Shared UI components for all apps          | Button, Input, Modal               | Generic components only              |
| Design Tokens            | Centralized colors, spacing, typography    | Never hardcode values              | Enables theming                      |
| Storybook                | Isolated component development             | Documentation + testing            | Great for large teams                |
| Semantic Versioning      | Version Design System safely               | Patch / Minor / Major              | Prevent breaking consumers           |
| Theming                  | Apply styles using tokens                  | Light/Dark themes                  | Components shouldn't know colors     |
| Component Ownership      | Decide where components live               | Feature vs Shared vs Design System | Biggest architecture discussion      |

## 10.4 Large Scale Frontend
| Question                          | Best Answer                                                       |
| --------------------------------- | ----------------------------------------------------------------- |
| Monorepo or Polyrepo?             | Depends on team coupling and shared code.                         |
| Nx or Turborepo?                  | Nx for large enterprises; Turborepo for simpler React ecosystems. |
| Module Federation solves?         | Runtime sharing and independent deployments.                      |
| npm package vs Module Federation? | Build-time reuse vs runtime reuse.                                |
| What should be shared?            | Design System, auth, API client, analytics, utilities.            |
| What should NOT be shared?        | Business features like Cart, Orders, Checkout.                    |
| Biggest MFE mistake?              | Splitting by UI instead of business domains.                      |
| Share Redux across MFEs?          | Generally no; share only minimal global state if needed.          |
| React version conflict?           | Use singleton shared dependencies and align versions.             |
| When NOT to use MFEs?             | Small teams, single product, infrequent deployments.              |
| Independent deployment?           | Core benefit of Module Federation and Micro Frontends.            |

## 10.5 Enterprise Decisions
| Question                        | Best Answer                                                 |
| ------------------------------- | ----------------------------------------------------------- |
| Folder structure?               | Choose based on team size and business domains.             |
| Business logic?                 | Hooks/Services, not components.                             |
| Server state?                   | React Query.                                                |
| UI state?                       | Local State or Context.                                     |
| API strategy?                   | Service → Repository → API.                                 |
| Authentication?                 | Provider + Token Manager + Interceptors.                    |
| First performance optimization? | Code splitting and caching, not `useMemo`.                  |
| Team ownership?                 | Business capabilities, not UI widgets.                      |
| Biggest architecture principle? | Separate responsibilities and organize by business domains. |



