## 9.1 Testing Fundamentals
| Topic                        | One-line Definition                                                            | Example                                         |
| ---------------------------- | ------------------------------------------------------------------------------ | ----------------------------------------------- |
| **Why Testing?**             | Ensures new changes don't break existing functionality (prevents regressions). | Login still works after adding Google Login     |
| **Unit Test**                | Tests one isolated unit (function, hook, or component).                        | Discount calculator, Button component           |
| **Integration Test**         | Tests multiple components/modules working together.                            | Login Form → Validation → API → Success Message |
| **E2E Test**                 | Tests the complete application flow like a real user.                          | Login → Search → Cart → Checkout → Payment      |
| **Testing Pyramid**          | Many Unit Tests → Some Integration Tests → Few E2E Tests.                      | Unit > Integration > E2E                        |
| **Behavior Testing**         | Test what the user sees and does.                                              | Button becomes disabled after clicking          |
| **Implementation Testing ❌** | Tests internal implementation details (avoid).                                 | Checking `useState` values directly             |
| **What NOT to Test**         | Don't test React, third-party libraries, or trivial code.                      | Material UI Button, constants, interfaces       |

| Test Type       | Question it Answers                   |
| --------------- | ------------------------------------- |
| **Unit**        | **Does this one thing work?**         |
| **Integration** | **Do these things work together?**    |
| **E2E**         | **Can the user complete their goal?** |


## 9.2 Jest 9.3 React Testing Library (RTL)

## 9.4 Testing React Applications
| Scenario              | What to Test         | What NOT to Test                                      |
| --------------------- | -------------------- | ----------------------------------------------------- |
| Props                 | Rendered UI          | Raw prop values                                       |
| State                 | Updated UI           | `useState` value                                      |
| Conditional Rendering | Correct branch shown | Internal conditions                                   |
| Events                | User-visible outcome | Internal function calls (unless it's a callback prop) |
| Buttons               | Click behavior       | CSS implementation                                    |

| Dependency                 | Mock? | Why                        |
| -------------------------- | ----- | -------------------------- |
| Backend API                | ✅     | Fast & predictable         |
| Callback Function          | ✅     | Verify interaction         |
| Utility Module             | ✅     | Isolate component          |
| Timer                      | ✅     | Avoid waiting              |
| Date                       | ✅     | Stable tests               |
| React Component Under Test | ❌     | That's what you're testing |

| Dependency     | Testing Strategy              |
| -------------- | ----------------------------- |
| ThemeContext   | Wrap Provider                 |
| AuthContext    | Wrap Provider                 |
| Router         | Wrap Router                   |
| Custom Hook    | Test Hook directly            |
| Error Boundary | Throw error → Verify fallback |


## 9.5 Snapshot Testing
| Snapshot Testing         | Behavior Testing        |
| ------------------------ | ----------------------- |
| Compares rendered output | Tests user interactions |
| Good for static UI       | Good for dynamic UI     |
| Detects visual changes   | Detects functionality   |
| Fast                     | More meaningful         |

## 9.6 End-to-End Testing
| Type        | Tests                  | Example                       |
| ----------- | ---------------------- | ----------------------------- |
| Unit        | One function/component | Discount calculator           |
| Integration | Multiple components    | Login Form + Validation + API |
| E2E         | Complete application   | Login → Checkout              |

| Playwright                   | Cypress                        |
| ---------------------------- | ------------------------------ |
| Better cross-browser support | Excellent developer experience |
| Faster parallel execution    | Great debugging/time travel    |
| Growing adoption             | Mature ecosystem               |

## 9.7 Enterprise Testing Strategy

| Mistake                      | Better Approach                   |
| ---------------------------- | --------------------------------- |
| Too many E2E tests           | Prefer Unit + Integration         |
| Testing internal state       | Test UI behavior                  |
| Mocking everything           | Mock only external dependencies   |
| Snapshot testing large pages | Snapshot only reusable components |
| One huge test                | Many focused tests                |


| Situation             | Best Choice           |
| --------------------- | --------------------- |
| Pure function         | Unit                  |
| Component interaction | Integration           |
| Full user journey     | E2E                   |
| Backend dependency    | Mock                  |
| Business logic        | Test for real         |
| Internal React state  | ❌ Don't test directly |
| User-visible behavior | ✅ Always test         |
