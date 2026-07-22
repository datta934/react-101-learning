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
