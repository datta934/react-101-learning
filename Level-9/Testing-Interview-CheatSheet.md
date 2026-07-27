## 1. Testing Pyramid

  Test Type     Tests                    Fast?   Real Browser?   Example
  ------------- ------------------------ ------- --------------- ---------------------
  Unit          One function/component   ✅      ❌              Discount Calculator
  Integration   Multiple components      ⚡      ❌              Login Form
  E2E           Complete application     ❌      ✅              Checkout Flow

**Key answer:** Most tests should be Unit Tests, fewer Integration
Tests, and only critical business journeys should be E2E.

## 2. Jest vs React Testing Library

  Jest          React Testing Library
  ------------- -----------------------------
  Test Runner   UI Testing Library
  Runs tests    Renders React Components
  Mocking       User interactions & queries

**One-liner:** Jest runs the tests, React Testing Library tests
components from the user's perspective.

## 3. Test Structure

  API            Purpose
  -------------- ------------------------
  describe()     Group tests
  test()/it()    One test
  expect()       Assertion
  beforeEach()   Runs before every test
  afterEach()    Cleanup

## 4. RTL APIs

  API         Use
  ----------- ----------------------
  render()    Render Component
  screen      Find Elements
  userEvent   Simulate User
  fireEvent   Low-level DOM Events

## 5. Queries

  Query     Use When
  --------- --------------------------
  getBy     Element already exists
  queryBy   Element should NOT exist
  findBy    Wait for async element

Memory: - getBy → Already exists - queryBy → Should not exist - findBy →
Appears later

## 6. Query Priority

1.  getByRole
2.  getByLabelText
3.  getByPlaceholderText
4.  getByText
5.  getByDisplayValue
6.  getByTestId (last choice)

## 7. userEvent vs fireEvent

  userEvent               fireEvent
  ----------------------- --------------------
  Real user interaction   Single DOM event
  Preferred               Legacy / low-level
  Async                   Immediate

## 8. Mocking

Mock: - APIs - Timers - Dates - Analytics - Payment Gateway

Don't Mock: - Business Logic - Reducers - Validators - Utility Functions

Rule: - Your code → Test it - External dependency → Mock it

## 9. Component Testing

Always test: - Props - User interactions - Conditional rendering -
Loading state - Error state

Don't test: - useState - Internal variables - CSS classes

## 10. Snapshot Testing

Good: - Button - Badge - Avatar - Icon

Avoid: - Dashboard - Checkout - Chat - Live data

## 11. Context Testing

Provider → Component → Assertions

## 12. Hook Testing

Common hooks: - useAuth - useCart - usePagination - useDebounce -
useLocalStorage

## 13. Router Testing

Don't test React Router itself. Test navigation to the correct page.

## 14. E2E

Automate: - Login - Registration - Checkout - Payment - Logout

Avoid: - Hover effects - CSS - Tooltips - Animations

## 15. Playwright vs Cypress

  Playwright               Cypress
  ------------------------ -----------------
  Cross-browser            Excellent DX
  Better parallelization   Great debugging
  Multi-tab support        Simpler setup

## 16. What should be tested?

  Feature               Test Type
  --------------------- -------------
  Discount Calculator   Unit
  Login Form            Integration
  Search Filters        Integration
  Checkout              E2E
  Payment               E2E
  Theme Switch          Integration

## 17. CI/CD

Commit → Unit → Integration → Build → QA → E2E → Production

## 18. Frequently Asked Interview Questions

**Why RTL over Enzyme?** - Tests behavior from the user's perspective.

**Why test behavior instead of implementation?** - Users interact with
UI, not internal state.

**Why mock APIs?** - Fast, deterministic, independent tests.

**Unit vs Integration vs E2E?** - Unit = one unit. - Integration =
multiple units. - E2E = complete user journey.

**What would you mock?** - APIs, timers, analytics, payment gateways. -
Not business logic.

**How do you avoid flaky tests?** - Mock unstable services. - Avoid
arbitrary timeouts. - Use proper async waiting. - Keep tests
independent. - Use stable selectors.

## 30-Second Revision

-   Jest → Runs tests
-   RTL → Tests like a user
-   getBy → Exists
-   queryBy → Doesn't exist
-   findBy → Async
-   Mock → External dependencies
-   Test → Business logic
-   Unit → Functions
-   Integration → Components
-   E2E → User journey
