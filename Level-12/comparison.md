# Level 12.7 — Pattern Comparison

---

# 1. Container Pattern vs Custom Hooks

| Container Pattern | Custom Hooks |
|-------------------|-------------|
| Business logic inside a wrapper component | Business logic inside a reusable hook |
| Creates extra wrapper components | No additional wrapper |
| Older React approach | Modern React approach |
| Harder to compose | Easier to compose |
| UI and logic separated by components | UI and logic separated by hooks |

### Use Container Pattern
- Maintaining legacy React applications
- Existing codebases already using the pattern

### Use Custom Hooks
- New React applications
- Reusing business logic
- Cleaner architecture

---

# 2. Higher Order Components (HOC) vs Render Props

| HOC | Render Props |
|------|--------------|
| Wraps a component | Passes a function |
| Returns an enhanced component | Returns JSX |
| Easier API | More UI flexibility |
| Can create Wrapper Hell | Can create Callback Hell |
| Good for cross-cutting concerns | Good for reusable rendering logic |

### Use HOC
- Authentication
- Authorization
- Analytics
- Logging
- Legacy libraries

### Use Render Props
- Legacy libraries
- Flexible rendering requirements

---

# 3. Render Props vs Custom Hooks

| Render Props | Custom Hooks |
|--------------|--------------|
| Function passed as a prop | Function called directly |
| Nested JSX | Cleaner syntax |
| More wrapper components | No wrappers |
| Legacy pattern | Modern React |
| Logic + render function | Logic only |

### Recommendation

Prefer **Custom Hooks** for all new React applications.

---

# 4. Compound Components vs Headless Components ⭐⭐⭐⭐⭐

| Compound Components | Headless Components |
|---------------------|--------------------|
| Creates a flexible component API | Provides reusable behavior |
| Parent coordinates children | No UI opinion |
| Usually built using Context | Usually built using Hooks + Context |
| Includes component structure | Lets consumers create their own structure |
| Often includes default UI | UI completely controlled by developer |

### Compound Components

Examples

- Tabs
- Accordion
- Modal
- Dropdown
- Select

### Headless Components

Examples

- Radix UI
- Headless UI
- React Aria

### Recommendation

Use **Compound Components** when building reusable component APIs.

Use **Headless Components** when consumers must completely control the UI.

---

# 5. Provider Pattern vs React Context

| React Context | Provider Pattern |
|---------------|------------------|
| React API | Design pattern |
| Mechanism | Architecture |
| Shares values | Organizes shared state |
| Built into React | Built using Context |

### Remember

> Context is the API.

> Provider Pattern is the architecture built on top of Context.

---

# 6. Provider Pattern vs Redux

| Provider Pattern | Redux |
|------------------|--------|
| Built into React | External library |
| Simple global state | Complex application state |
| Less boilerplate | More features |
| Easier setup | Better debugging tools |
| Good for small/medium apps | Better for very large applications |

### Provider Examples

- Theme
- Authentication
- Locale
- Feature Flags

### Redux Examples

- Shopping Cart
- Banking Dashboard
- Enterprise Workflows
- Offline Synchronization

---

# 7. Provider Pattern vs React Query

| Provider Pattern | React Query |
|------------------|-------------|
| Client/UI State | Server State |
| Authentication | Products API |
| Theme | Orders API |
| Language | User API |
| Feature Flags | Inventory API |

### Remember

React Query **does not replace Context**.

They solve different problems.

---

# 8. Headless Components vs Component Libraries

| Headless Components | Traditional UI Libraries |
|----------------------|--------------------------|
| Logic only | Logic + Styling |
| Full UI customization | Fixed visual design |
| Design-system friendly | Ready-to-use UI |
| Accessibility included | Accessibility included |
| Build your own appearance | Use provided appearance |

### Headless Libraries

- Radix UI
- Headless UI
- React Aria

### Traditional UI Libraries

- Material UI
- Ant Design
- Chakra UI
- Mantine

---

# 9. Pattern Selection Decision Tree ⭐⭐⭐⭐⭐

```
Need reusable business logic?

↓

Custom Hook

────────────────────────────

Need shared application state?

↓

Provider Pattern

────────────────────────────

Need flexible component APIs?

↓

Compound Components

────────────────────────────

Need reusable logic without UI?

↓

Headless Components

────────────────────────────

Maintaining older React projects?

↓

HOC / Render Props
```

---

# 10. Modern React Recommendations

| Pattern | Recommendation |
|----------|----------------|
| Container Pattern | Understand the concept |
| HOC | Legacy but still asked |
| Render Props | Legacy but still asked |
| Custom Hooks | ⭐⭐⭐⭐⭐ Daily use |
| Compound Components | ⭐⭐⭐⭐⭐ Must know |
| Provider Pattern | ⭐⭐⭐⭐⭐ Must know |
| Headless Components | ⭐⭐⭐⭐⭐ Must know |

---

# Quick Interview Cheat Sheet

| Question | Best Answer |
|----------|-------------|
| Reuse business logic? | Custom Hooks |
| Share global application state? | Provider Pattern |
| Build reusable component APIs? | Compound Components |
| Build design system primitives? | Headless Components |
| Maintaining legacy React? | HOC / Render Props |
| Simple app-wide state? | Context + Provider |
| Complex enterprise state? | Redux (or equivalent) |
| Server state? | React Query |

---

# Modern React Evolution

```
Container Pattern
        │
        ▼
Higher Order Components (HOC)
        │
        ▼
Render Props
        │
        ▼
Custom Hooks
        │
        ▼
Compound Components
        │
        ▼
Provider Pattern
        │
        ▼
Headless Components
```