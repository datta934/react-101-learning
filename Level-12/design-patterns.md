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
