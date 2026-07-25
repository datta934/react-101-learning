## 6.1 Form Fundamentals

| Controlled                   | Uncontrolled               |
| ---------------------------- | -------------------------- |
| React owns value             | DOM owns value             |
| Uses state                   | Uses ref/FormData          |
| More re-renders              | Fewer re-renders           |
| Easier validation            | Harder validation          |
| Easier conditional UI        | Simpler code               |
| Preferred for business forms - Login, Bank transfer | Preferred for simple cases - Newsletter, Search (not live) |

## 6.2 Validation

| Concept                    | One-line Definition                                             | Example                                                          | Why it Matters                                            |
| -------------------------- | --------------------------------------------------------------- | ---------------------------------------------------------------- | --------------------------------------------------------- |
| **Client-side Validation** | Validation performed in the browser before submitting the form. | Email format, required fields, password length.                  | Faster UX, reduces unnecessary API calls.                 |
| **Server-side Validation** | Validation performed on the backend after form submission.      | Username already exists, payment declined, insufficient balance. | Security and data integrity. Always required.             |
| **Async Validation**       | Validation that requires an API call to verify data.            | Check username availability, validate coupon code.               | Information is only available from the server.            |
| **Schema Validation**      | Define all validation rules in one reusable schema.             | Yup/Zod schema for a registration form.                          | Centralized, reusable, and maintainable validation logic. |
| **Validation UX**          | Decide **when** and **how** validation messages are shown.      | Password strength on change, email validation on blur.           | Better user experience without annoying users.            |

## 6.3 React Hook Form
Instead of React controlling every input, let the browser manage the input value and only notify React when needed.
| API               | Purpose                                     | Example                      |
| ----------------- | ------------------------------------------- | ---------------------------- |
| `useForm()`       | Creates the form controller                 | Registration form            |
| `register()`      | Register native inputs                      | Name, Email, Password        |
| `handleSubmit()`  | Validate and submit                         | Login form                   |
| `Controller`      | Connect third-party controlled components   | MUI DatePicker, React Select |
| `FormProvider`    | Share form methods across nested components | Checkout wizard              |
| `useFieldArray()` | Manage dynamic lists                        | Skills, Addresses            |

| Question                                   | Answer                                                                                                                                                                      |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Why is React Hook Form faster?**         | RHF uses **uncontrolled inputs** by default, so typing doesn't update React state on every keystroke. It minimizes unnecessary re-renders, making it ideal for large forms. |
| **When do you use `register()`?**          | For **native HTML inputs** like `<input>`, `<textarea>`, `<select>`.                                                                                                        |
| **When do you use `Controller`?**          | For **third-party controlled components** that don't expose a native input, e.g., Material UI DatePicker, React Select, Ant Design components.                              |
| **What does `useForm()` do?**              | It creates and manages the form. It provides methods for registration, validation, submission, errors, reset, and form state.                                               |
| **What does `handleSubmit()` do?**         | It prevents default form submission, validates the form, collects values, and calls your submit function only if validation passes.                                         |
| **What does `FormProvider` solve?**        | It shares form methods with deeply nested components, eliminating prop drilling in large forms.                                                                             |
| **When do you use `useFieldArray()`?**     | When users can dynamically add or remove fields, e.g., skills, work experience, phone numbers, education, addresses.                                                        |
| **When would you choose React Hook Form?** | Large enterprise forms, complex validation, dynamic forms, and performance-sensitive applications.                                                                          |
| **When is plain React enough?**            | Small forms like login, contact us, newsletter signup, or simple search forms.                                                                                              |

## 6.4 Formik
| Feature                              | React Hook Form        | Formik                       |
| ------------------------------------ | ---------------------- | ---------------------------- |
| Input Type                           | Uncontrolled (default) | Controlled                   |
| Performance                          | ⭐⭐⭐⭐⭐                  | ⭐⭐⭐                          |
| Re-renders                           | Minimal                | More frequent                |
| Validation                           | Built-in + Yup/Zod     | Usually Yup                  |
| Bundle Size                          | Smaller                | Larger                       |
| Learning Curve                       | Slightly steeper       | Easier initially             |
| Enterprise Popularity (modern React) | Very High              | Legacy projects / still used |
| Biggest Difference | DOM owns input -> Minimal Re-renders           | React owns input -> More Re-renders |

## 6.5 Dynamic Forms
| Pattern               | Definition                                  | Example                    | React Hook Form Feature    |
| --------------------- | ------------------------------------------- | -------------------------- | -------------------------- |
| **Dynamic Fields**    | User can add/remove inputs                  | Skills, Work Experience    | `useFieldArray()`          |
| **Nested Forms**      | Split one large form into reusable sections | Checkout, Employee Form    | `FormProvider`             |
| **Multi-step Forms**  | Form divided into sequential pages          | Loan Application, Checkout | Step-based validation      |
| **JSON-driven Forms** | Form generated from backend configuration   | Survey Builder, CMS        | Dynamic rendering + schema |




