## 4.1 State Fundamentals

| Concept                    | Purpose                                | Who Owns It?              | Real-world Examples                             | Remember               |
| -------------------------- | -------------------------------------- | ------------------------- | ----------------------------------------------- | ---------------------- |
| **Local State**            | State used by only one component       | Same Component            | Hover, Modal Open, Selected Tab, Tooltip        | **Only I need it**     |
| **Lift State Up**          | Share state between sibling components | Nearest Common Parent     | Quantity + Add to Cart, SearchBar + ProductList | **Shared by siblings** |
| **Component State**        | Data managed by a component            | Same Component            | Accordion, Dropdown, Input Value                | Same as Local State    |
| **UI State**               | Controls appearance                    | Usually Local or Context  | Theme, Modal, Sidebar, Tooltip                  | **How it LOOKS**       |
| **Business State**         | Controls application behavior          | Context / Redux / Zustand | User, Cart, Orders, Permissions                 | **How it WORKS**       |
| **Controlled Component**   | React controls the input               | React State               | `<input value={name} />`                        | React owns value       |
| **Uncontrolled Component** | Browser controls the input             | DOM                       | `<input ref={inputRef} />`                      | DOM owns value         |
| **Ephemeral State**        | Short-lived UI state                   | Local Component           | Hover, Loading Spinner, Drag Position           | Dies on unmount        |
| **Single Source of Truth** | One place owns the data                | One Component/Store       | Cart, User, Theme                               | Never duplicate state  |

### <u>State decision tree</u>
| Situation                              | Best Choice             | Example                         |
| -------------------------------------- | ----------------------- | ------------------------------- |
| Only one component needs it            | Local State             | Modal Open                      |
| Two or more sibling components need it | Lift State Up           | Quantity Selector + Add To Cart |
| Many nested components need it         | Context API             | Theme, Language, Auth           |
| Whole application needs it             | Redux / Zustand         | Cart, User, Notifications       |
| Server owns the data                   | RTK Query / React Query | Products, Orders, Profile       |


## 4.2 Context API
<img width="1536" height="1024" alt="4 2" src="https://github.com/user-attachments/assets/d9ad6c2a-c078-427f-9c74-9ce42186f9c6" />


## 4.3 useReducer
<img width="1536" height="1024" alt="4 3" src="https://github.com/user-attachments/assets/d8b13f5a-1860-4039-8fb3-1b93a73be06c" />

## 4.4 Redux Toolkit (RTK)
<img width="1536" height="1024" alt="4 4" src="https://github.com/user-attachments/assets/4f681feb-133e-43ee-8188-9a13c8cf4535" />

## 4.5 RTK Query
<img width="1536" height="1024" alt="4 5" src="https://github.com/user-attachments/assets/8346737e-572f-4bc6-911d-b9e8775fcdcd" />

## 4.6-4.8 Zustand, Jotai & MobX

### Definition

| Library           | Philosophy                    | Best For                  | Mental Model                               |
| ----------------- | ----------------------------- | ------------------------- | ------------------------------------------ |
| **Redux Toolkit** | Predictable centralized state | Large enterprise apps     | One centralized store with reducers        |
| **Zustand**       | Minimal global state          | Most modern React apps    | `useState` for the whole app               |
| **Jotai**         | Atomic state                  | Complex independent state | Everything is an Atom                      |
| **MobX**          | Reactive OOP                  | Enterprise/OOP teams      | Observable objects automatically update UI |

### Comparison

| Feature              | Redux Toolkit | Zustand   | Jotai     | MobX      |
| -------------------- | ------------- | --------- | --------- | --------- |
| Boilerplate          | High          | Very Low  | Low       | Low       |
| Learning Curve       | Medium        | Easy      | Medium    | Medium    |
| DevTools             | Excellent     | Good      | Good      | Good      |
| Performance          | Excellent     | Excellent | Excellent | Excellent |
| Predictability       | Excellent     | Good      | Good      | Medium    |
| Automatic Reactivity | ❌             | ❌         | ❌         | ✅         |
| Best for Enterprise  | ⭐⭐⭐⭐⭐         | ⭐⭐⭐⭐      | ⭐⭐⭐       | ⭐⭐⭐⭐      |

### When to choose what

| Scenario                 | Best Choice             | Why                            |
| ------------------------ | ----------------------- | ------------------------------ |
| Small App                | Context                 | Simple shared state            |
| Medium App               | Zustand                 | Fast setup, little boilerplate |
| Large Enterprise         | Redux Toolkit           | Structure and predictability   |
| Highly Independent State | Jotai                   | Atomic updates                 |
| Finance / ERP            | MobX                    | Reactive business logic        |
| API Data                 | RTK Query / React Query | Server state                   |


## 4.9 Server State
<img width="1536" height="1024" alt="4 9" src="https://github.com/user-attachments/assets/287824c2-4c6e-4a08-9040-5b3ba2b34786" />
