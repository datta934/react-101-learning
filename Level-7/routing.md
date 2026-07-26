## 7.1 Routing Fundamentals and 7.2 Nested Routing
<img width="1536" height="1024" alt="7 2" src="https://github.com/user-attachments/assets/344427f1-f175-4401-ba0e-6dd5e61d2430" />

## 7.3 Protected Routing
<img width="1536" height="1024" alt="7 3" src="https://github.com/user-attachments/assets/2cd20a30-2d83-4dc2-b9a8-2952616477a6" />

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
