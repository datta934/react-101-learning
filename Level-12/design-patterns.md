## 12.1 Container / Presentational Pattern
- Oldest pattern
- It separates business logic and data management from UI rendering. The container handles fetching data and state, while the presentational component focuses only on displaying the UI.
- When should you use it? Large UI, Complex API calls, Reusable UI, Multiple data sources
- When not to use it? Small component 
- Modern React typically replaces container components with custom hooks, while presentational components remain focused on rendering.
- Hooks replace Container Components - Hooks allow us to reuse stateful logic without introducing extra wrapper components.

>"The principle of separating UI from business logic is still fundamental. Modern React achieves it more elegantly through custom hooks instead of dedicated container components."

## 12.2 Higher Order Components (HOC)
- A Higher Order Component is a function that takes a component and returns a new component with additional functionality.
- Why did Hooks replace HOCs?
    - reduce wrapper components
    - improve readability
    - simplify debugging
    - avoid wrapper hell
    - allow logic reuse without changing the component tree

| Topic              | Remember                                    |
| ------------------ | ------------------------------------------- |
| HOC                | Function that returns an enhanced component |
| Main Purpose       | Reuse cross-cutting behavior                |
| Examples           | Auth, Logging, Analytics                    |
| Biggest Drawback   | Wrapper Hell                                |
| Modern Replacement | Custom Hooks                                |
| Still Asked?       | Yes, especially in senior interviews        |

>"HOCs remain important to understand because many enterprise applications and older libraries use them. However, for new React development, I generally prefer custom hooks since they provide the same logic reuse without adding wrapper components."


## 12.3 Render props
- Just like HOCs, Render Props were invented to reuse logic.
- A prop whose value is a function that returns JSX.
- Example:
```javascript
<MouseTracker
    render={(mouse) => (
        <div>
            {mouse.x}
        </div>
    )}
/>
```
- MouseTracker owns State, Logic. You decide UI
- Hooks replace render props - Hooks provide the same logic reuse with significantly less nesting, better readability, and a simpler component tree.

>"Would you choose HOC or Render Props today?" --> "Neither for a new React application. I would generally choose a custom hook because it separates reusable logic from UI without introducing wrapper components or nested render functions. However, I'm comfortable working with both HOCs and Render Props when maintaining existing enterprise codebases."


| Generation | Pattern                  | Modern Status         |
| ---------- | ------------------------ | --------------------- |
| 1          | Container/Presentational | Principle still valid |
| 2          | Higher Order Components  | Mostly legacy         |
| 3          | Render Props             | Mostly legacy         |
| 4          | Custom Hooks             | ✅ Current standard    |

## 12.4 Compound Components
- A group of related components that work together by sharing an internal state managed by a common parent.
- Example: The parent owns the state. Children just participate.
- Excellent for Design Systems
```javascript
<Tabs>
    <Tabs.List />
    <Tabs.Tab />
    <Tabs.Panel />
</Tabs>
```

>"When building reusable components like Tabs, Accordions, or Modals for a design system, I prefer the Compound Component pattern because it creates a clean, composable API and scales much better than passing dozens of props."

## 12.5 Provider Pattern
- Strong familarity with Angular Dependency Injection
- Provide it once. Consume it anywhere. Exammple: AuthProvider
- Exposes shared state or services to multiple components using React Context.

>Compound Components use Context internally to coordinate their children. Provider Pattern is about exposing shared application state (theme, auth, locale, etc.) to many unrelated components.

> "I use Providers only for shared application concerns such as authentication, theming, localization, and feature flags. I avoid putting frequently changing local UI state into Context because every Provider update can trigger re-renders for its consumers. I also prefer composing multiple focused Providers instead of creating one large global context."

## 12.6 Headless components
- A Headless Component provides behavior and state but does not provide any UI.
- You decide: HTML, CSS, Layout
- The component provides: Logic, Accessibility, Keyboard support, State
- Headless Components combine: Context, Compound Components, Custom Hooks
- Drawbacks - Need to build all styling. Unlike Material UI.

> "What pattern would you use when building a reusable component library?" - "I'd combine several patterns. I'd use Compound Components to create an intuitive API, Context internally to share state between related components, and expose the behavior as Headless Components so product teams can build their own branded UI while reusing the same accessible logic."

## 12.7 [Comparison](comparison.md)

## 12.8 Legacy & Related Patterns

>"React itself primarily follows composition over inheritance. Modern React encourages Custom Hooks for logic reuse, Compound Components for flexible APIs, Provider Pattern for shared state, and Headless Components for reusable behavior. General software patterns like Repository, Factory, Observer, and Singleton still have their place around the React application, but they aren't React-specific patterns."

| Pattern                          | One-Line Definition                                                   | Primary Purpose                     | Typical Examples                                            | Modern Status                                                  | Interview Answer (30-second version)                                                                                                                                           |
| -------------------------------- | --------------------------------------------------------------------- | ----------------------------------- | ----------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Container / Presentational**   | Separates business logic from UI rendering.                           | Separation of concerns              | ProductContainer → ProductCard, UserContainer → UserProfile | 🟡 Concept still relevant (Hooks replaced explicit containers) | *"It separates data fetching and business logic from presentation. Today I usually achieve the same separation using Custom Hooks instead of dedicated container components."* |
| **Higher Order Component (HOC)** | A function that takes a component and returns an enhanced component.  | Reuse cross-cutting behavior        | `withAuth()`, `withLoading()`, `withPermission()`           | 🟡 Legacy                                                      | *"HOCs wrap components to add reusable behavior like authentication or logging. Modern React usually prefers Custom Hooks for the same purpose."*                              |
| **Render Props**                 | A component shares logic by calling a function prop that returns JSX. | Reuse stateful logic                | MouseTracker, DataProvider, older Formik APIs               | 🟡 Legacy                                                      | *"Render Props allow reusable logic while letting the caller decide how to render the UI. Hooks provide the same benefit with much cleaner syntax."*                           |
| **Custom Hooks**                 | A reusable function that encapsulates React stateful logic.           | Logic reuse                         | `useAuth()`, `useProducts()`, `useFetch()`                  | 🟢 Recommended                                                 | *"Custom Hooks are the preferred modern way to reuse React logic without introducing wrapper components."*                                                                     |
| **Compound Components**          | Multiple related components share state through a common parent.      | Flexible component APIs             | Tabs, Accordion, Modal, Select                              | 🟢 Recommended                                                 | *"Compound Components create expressive APIs where related child components share parent state, usually through Context."*                                                     |
| **Provider Pattern**             | Shares application-wide state using React Context.                    | Global/shared state                 | ThemeProvider, AuthProvider, LocaleProvider                 | 🟢 Recommended                                                 | *"Provider Pattern exposes shared application state like authentication or themes without prop drilling."*                                                                     |
| **Headless Components**          | Provides behavior and accessibility without providing UI.             | Reusable logic with customizable UI | Radix UI, Headless UI, React Aria                           | 🟢 Recommended                                                 | *"Headless Components separate behavior from presentation, allowing complete UI customization while reusing accessible logic."*                                                |
| **Repository Pattern**           | Abstracts data access behind a consistent interface.                  | Decouple API/database access        | `ProductRepository`, `UserRepository`                       | 🟢 Enterprise Pattern                                          | *"Repositories isolate data access so UI components remain independent of backend implementation details."*                                                                    |
| **Factory Pattern**              | Centralizes object or component creation.                             | Dynamic creation                    | Dynamic Forms, Component Factory, Widget Factory            | 🟢 General Design Pattern                                      | *"Factory Pattern creates objects or components without exposing creation logic, making systems easier to extend."*                                                            |
| **Observer Pattern**             | Subscribers automatically react when data changes.                    | Event notification                  | React state updates, Redux, RxJS, Event Bus                 | 🟢 General Design Pattern                                      | *"Observer Pattern lets multiple subscribers respond automatically when shared state changes."*                                                                                |
| **Singleton Pattern**            | Ensures only one shared instance exists.                              | Shared services                     | Axios Client, Logger, Analytics SDK, Auth Service           | 🟢 General Design Pattern                                      | *"Singleton guarantees a single shared instance across the application, commonly used for API clients and logging."*                                                           |
