### generic rules

* Implement a single, high-level layout for all Admin Portal interfaces. Centralize reusable components (settings, user avatar) within it. Child screens must only provide their unique content, inheriting the shared layout.
* Implement clear UI states for loading, errors, and empty data in all components and pages. Never assume data is instantly available or always successful.
* For all applications, create standard screens for authentication, user profile management (with synchronized avatar), and application settings (including theme and data persistence control).
* Always implement data grids as separate components. Pass data to them as props—keep data fetching and state management in the parent page.
* Establish a core component library (buttons, toasts, labels) with consistent, theme-driven styling. Reuse these components universally and prohibit inline styling.


