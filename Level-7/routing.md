## 7.1 Routing Fundamentals and 7.2 Nested Routing

## 7.3 Protected Routing

## 7.4 Lazy Routes
Lazy Route
```javascript
const Orders = lazy(() => import("./Orders"));`
```
Suspense
```javascript
<Suspense fallback={<Loader />}>
    <Orders />
</Suspense>
```

Active Navigation
```javascript
<NavLink to="/orders">
    Orders
</NavLink>
```

Route-based Lazy Loading
```javascript
<Route path="/orders" element={<Orders />} />
```

## 7.5 Navigation Patterns
| Requirement            | Solution           |
| ---------------------- | ------------------ |
| Large dashboard        | Lazy load routes   |
| Shared sidebar         | NavLink            |
| User hierarchy         | Breadcrumbs        |
| Related sections       | Tabs               |
| Different user roles   | Dynamic navigation |
| Shareable URLs         | Deep linking       |
| Preserve user position | Scroll restoration |
